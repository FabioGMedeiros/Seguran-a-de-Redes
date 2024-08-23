
# Segurança de Redes

## 1. O que é encriptação tripla?

Encriptação tripla, ou **Triple DES (3DES)**, é uma versão mais segura do algoritmo de criptografia Data Encryption Standard (DES). O 3DES aplica o algoritmo DES três vezes a cada bloco de dados, usando três chaves diferentes. Existem várias formas de implementação do 3DES, sendo a mais comum conhecida como **EDE (Encrypt-Decrypt-Encrypt)**, que significa que os dados são criptografados, depois descriptografados, e então criptografados novamente.

## 2. O que é ataque meet-in-the-middle?

O **ataque meet-in-the-middle** é um tipo de ataque criptográfico que pode ser aplicado a esquemas de criptografia que utilizam múltiplas camadas de cifragem, como o 3DES. Neste ataque, o atacante tenta quebrar a criptografia por meio de uma combinação de ataque de força bruta e comparação de resultados intermediários. O atacante primeiro criptografa o texto simples com uma chave e, ao mesmo tempo, tenta descriptografar o texto cifrado com outra chave. O objetivo é encontrar um valor intermediário que coincida, o que pode reduzir significativamente o esforço necessário para quebrar a criptografia, tornando-a menos segura do que o esperado.

## 3. Quantas chaves são usadas na encriptação tripla?

No **3DES**, podem ser usadas **duas ou três chaves**. Quando se usa três chaves diferentes, a segurança é máxima. No caso de duas chaves, a primeira e a terceira operação usam a mesma chave, o que ainda melhora a segurança em comparação ao DES simples, mas é menos seguro do que o 3DES com três chaves distintas.

## 4. Por que a parte do meio do 3DES é decriptação, em vez de encriptação?

A parte do meio do 3DES é uma **descriptografia** para garantir a compatibilidade com a versão original do DES. Se o 3DES fosse simplesmente três encriptações, ele não seria compatível com o DES simples. Mas, ao descriptografar no meio, se você usar a mesma chave para todas as três operações, o 3DES se comporta como uma única aplicação do DES, permitindo que sistemas que utilizam DES possam migrar para 3DES sem a necessidade de alterações significativas.

## 5. Por que alguns modos de operação de cifra de bloco só utilizam a encriptação, enquanto outros empregam encriptação e decriptação?

**Modos de operação de cifra de bloco** são técnicas que determinam como os blocos sucessivos de texto claro são processados durante a criptografia. Modos como o **Electronic Codebook (ECB)** e **Cipher Block Chaining (CBC)** utilizam a encriptação repetidamente para garantir a segurança. Em contraste, modos como o **Output Feedback (OFB)** e **Counter (CTR)** utilizam apenas a encriptação para gerar um fluxo de chave, que é então combinado com o texto claro (ou cifrado) para produzir o texto cifrado (ou claro). Esses modos só precisam de encriptação porque a operação inversa também pode ser realizada simplesmente reexecutando o processo de encriptação.

## 6. Escolha entre as abordagens apresentadas na Figura para 3DES no modo CBC:

### (a) Por segurança:

Escolhi a opção **(b) CBC com três loops** por ser mais segura. Esta abordagem utiliza três chaves distintas \( K_1 \), \( K_2 \), e \( K_3 \), aplicando encriptação, decriptação, e encriptação novamente em três etapas separadas. A complexidade adicional dessas operações, junto com a diversidade das chaves, torna a criptografia muito mais resistente a ataques criptográficos, como o meet-in-the-middle. Portanto, em termos de segurança, essa configuração é superior à opção de um único loop.

# Questão 7: Encriptação e Decriptação usando S-DES no Modo CBC

Para a questão proposta, foi desenvolvido um software que realiza a encriptação e decriptação no modo Cipher Block Chaining (CBC) utilizando o algoritmo S-DES (Simplified DES). A seguir está o código completo que implementa o S-DES e o modo CBC, e realiza o teste com os dados fornecidos.

## Código

```python
# Funções auxiliares para o S-DES (Simplified DES)

# Permutação P10, P8, P4, IP, IP-1, EP, S-Box S0, S1, etc.

def permute(original, permutation):
    return ''.join([original[i-1] for i in permutation])

def left_shift(bits, shift):
    return bits[shift:] + bits[:shift]

def s_box_lookup(input_bits, s_box):
    row = int(input_bits[0] + input_bits[3], 2)
    col = int(input_bits[1] + input_bits[2], 2)
    return format(s_box[row][col], '02b')

# Funções para S-DES

def generate_keys(key):
    # P10 Permutation
    p10 = [3, 5, 2, 7, 4, 10, 1, 9, 8, 6]
    key = permute(key, p10)
    
    # Split and perform left shift
    left, right = key[:5], key[5:]
    left, right = left_shift(left, 1), left_shift(right, 1)
    
    # P8 Permutation
    p8 = [6, 3, 7, 4, 8, 5, 10, 9]
    k1 = permute(left + right, p8)
    
    # Second round of left shifts
    left, right = left_shift(left, 2), left_shift(right, 2)
    k2 = permute(left + right, p8)
    
    return k1, k2

def f_k(bits, key):
    ep = [4, 1, 2, 3, 2, 3, 4, 1]
    s0 = [[1, 0, 3, 2], [3, 2, 1, 0], [0, 2, 1, 3], [3, 1, 3, 2]]
    s1 = [[0, 1, 2, 3], [2, 0, 1, 3], [3, 0, 1, 0], [2, 1, 0, 3]]
    p4 = [2, 4, 3, 1]
    
    # Initial split
    left, right = bits[:4], bits[4:]
    
    # EP expansion
    expanded_right = permute(right, ep)
    
    # XOR with key
    xor_result = format(int(expanded_right, 2) ^ int(key, 2), '08b')
    
    # S-box lookup
    left_sbox = s_box_lookup(xor_result[:4], s0)
    right_sbox = s_box_lookup(xor_result[4:], s1)
    
    # P4 permutation
    sbox_output = permute(left_sbox + right_sbox, p4)
    
    # XOR with left half
    result = format(int(left, 2) ^ int(sbox_output, 2), '04b') + right
    return result

def sdes_encrypt(plain_text, key):
    # Initial Permutation
    ip = [2, 6, 3, 1, 4, 8, 5, 7]
    ip_inv = [4, 1, 3, 5, 7, 2, 8, 6]
    plain_text = permute(plain_text, ip)
    
    # Generate keys
    k1, k2 = generate_keys(key)
    
    # Round 1
    left, right = plain_text[:4], plain_text[4:]
    temp = f_k(plain_text, k1)
    
    # Swap halves and apply round 2
    swapped = temp[4:] + temp[:4]
    cipher_text = f_k(swapped, k2)
    
    # Inverse Initial Permutation
    cipher_text = permute(cipher_text, ip_inv)
    
    return cipher_text

def sdes_decrypt(cipher_text, key):
    # Initial Permutation
    ip = [2, 6, 3, 1, 4, 8, 5, 7]
    ip_inv = [4, 1, 3, 5, 7, 2, 8, 6]
    cipher_text = permute(cipher_text, ip)
    
    # Generate keys
    k1, k2 = generate_keys(key)
    
    # Round 1 (using k2)
    left, right = cipher_text[:4], cipher_text[4:]
    temp = f_k(cipher_text, k2)
    
    # Swap halves and apply round 2 (using k1)
    swapped = temp[4:] + temp[:4]
    plain_text = f_k(swapped, k1)
    
    # Inverse Initial Permutation
    plain_text = permute(plain_text, ip_inv)
    
    return plain_text

# Funções CBC

def xor_bits(bits1, bits2):
    return format(int(bits1, 2) ^ int(bits2, 2), '08b')

def cbc_encrypt(plain_text, key, iv):
    blocks = [plain_text[i:i+8] for i in range(0, len(plain_text), 8)]
    cipher_text = ''
    previous_cipher_block = iv
    
    for block in blocks:
        block_to_encrypt = xor_bits(block, previous_cipher_block)
        encrypted_block = sdes_encrypt(block_to_encrypt, key)
        cipher_text += encrypted_block
        previous_cipher_block = encrypted_block
    
    return cipher_text

def cbc_decrypt(cipher_text, key, iv):
    blocks = [cipher_text[i:i+8] for i in range(0, len(cipher_text), 8)]
    plain_text = ''
    previous_cipher_block = iv
    
    for block in blocks:
        decrypted_block = sdes_decrypt(block, key)
        original_block = xor_bits(decrypted_block, previous_cipher_block)
        plain_text += original_block
        previous_cipher_block = block
    
    return plain_text

# Teste com os dados fornecidos

# Definindo as variáveis
plain_text = '0000000100100011'
key = '0111111101'
iv = '10101010'
expected_cipher_text = '1111010000001011'

# Encriptando
cipher_text = cbc_encrypt(plain_text, key, iv)
print(f'Texto Cifrado: {cipher_text} (Esperado: {expected_cipher_text})')

# Decriptando
decrypted_text = cbc_decrypt(cipher_text, key, iv)
print(f'Texto Decriptado: {decrypted_text} (Original: {plain_text})')
```
## Resultado do Teste

- **Texto Cifrado**: `1111010000001011` (Esperado: `1111010000001011`)
- **Texto Decriptado**: `0000000100100011` (Original: `0000000100100011`)
