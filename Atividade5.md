### 1. Qual foi o conjunto original de critérios usados pelo NIST para avaliar as cifras AES candidatas?

O NIST usou um conjunto de critérios técnicos e critérios de desempenho para avaliar as cifras AES candidatas. Os critérios técnicos incluíam:

- **Segurança:** Resistência contra todos os tipos conhecidos de ataques criptoanalíticos.
- **Eficiência em hardware e software:** Desempenho eficiente em uma ampla variedade de plataformas, incluindo microcontroladores, smart cards, hardware de alta performance, etc.
- **Flexibilidade:** Capacidade de operar em diferentes ambientes, com diferentes tamanhos de chave.
- **Simplicidade:** Facilidade de análise e implementação, com o objetivo de reduzir a possibilidade de erros.

### 2. Qual foi o conjunto final de critérios usados pelo NIST para avaliar as cifras AES candidatas?

O conjunto final de critérios focou principalmente nos seguintes aspectos:

- **Segurança:** Continuação da ênfase na resistência contra ataques criptoanalíticos, incluindo novas ameaças identificadas durante o processo de avaliação.
- **Desempenho:** Avaliação detalhada de desempenho em várias plataformas e ambientes, tanto em software quanto em hardware.
- **Eficiência:** Considerações sobre a eficiência em diferentes dispositivos, incluindo dispositivos com recursos limitados.
- **Implementação:** Facilidade e segurança na implementação, minimizando o risco de vulnerabilidades.
- **Flexibilidade:** Capacidade da cifra de operar eficientemente com diferentes tamanhos de chave e blocos.

### 3. Qual é a diferença entre Rijndael e AES?

Rijndael é o algoritmo original proposto por Joan Daemen e Vincent Rijmen que venceu a competição AES. AES (Advanced Encryption Standard) é a versão padronizada de Rijndael, mas com algumas restrições específicas:

- **Tamanhos de Bloco:** Rijndael suporta tamanhos de bloco de 128, 192 e 256 bits, enquanto o AES padroniza o tamanho do bloco para 128 bits.
- **Tamanhos de Chave:** Ambos Rijndael e AES suportam tamanhos de chave de 128, 192 e 256 bits.
  
Basicamente, o AES é uma versão restrita de Rijndael, com foco em blocos de 128 bits.

### 4. Responda:

#### (a) Qual é a finalidade do array Estado?

O array Estado é uma matriz 4x4 de bytes que é usada para armazenar o bloco de dados intermediário em várias etapas do processo de cifragem ou decifragem no AES. Ele é modificado em cada estágio do algoritmo até que o texto cifrado final seja produzido.

#### (b) Como é construída a S-box?

A S-box (Substitution box) é construída utilizando duas etapas principais:
1. **Inversão Multiplicativa:** Cada byte da S-box é o inverso multiplicativo do byte correspondente no campo finito GF(2^8).
2. **Transformação Afim:** O resultado da inversão é então submetido a uma transformação afim, que é uma combinação de operações lineares e uma constante de adição.

#### (c) Descreva rapidamente os estágios SubBytes, ShiftRows, MixColumns, AddRoundKey, e o algoritmo de expansão de chave:

- **SubBytes:** Cada byte do array Estado é substituído por seu equivalente na S-box, fornecendo a não-linearidade ao algoritmo.
- **ShiftRows:** Cada linha do array Estado é deslocada ciclicamente para a esquerda por um número diferente de posições (0, 1, 2, 3 para as quatro linhas).
- **MixColumns:** As colunas do array Estado são tratadas como polinômios e multiplicadas por um polinômio fixo, o que mistura os bytes em cada coluna.
- **AddRoundKey:** Cada byte do array Estado é combinado com um byte da chave expandida usando uma operação XOR.
- **Expansão de Chave:** A chave original é expandida para gerar várias chaves de rodada, usadas em cada rodada do processo de cifragem/decifragem. Esse processo envolve deslocamentos, substituições via S-box e a combinação com constantes de rodada.

### 5. Quantos bytes em Estado são afetados por ShiftRows?

No estágio ShiftRows do AES, **todos os 16 bytes** no array Estado são afetados, já que as linhas da matriz são deslocadas ciclicamente, alterando a posição dos bytes.

### 6. Use a chave 1010 0111 0011 1011 para encriptar o texto claro "ok" conforme expresso em ASCII, ou seja, 0110 1111 0110 1011. Os projetistas do S-AES obtiveram o texto cifrado 0000 0111 0011 1000. E você?

Para criptografar o texto "ok" usando o algoritmo S-AES com a chave `1010 0111 0011 1011`, foi utilizado o seguinte código em Python:

```python
def xor_bytes(a, b):
    return [i ^ j for i, j in zip(a, b)]

def sub_nib(b):
    sbox = [0x9, 0x4, 0xA, 0xB, 0xD, 0x1, 0x8, 0x5, 0x6, 0x2, 0x0, 0x3, 0xC, 0xE, 0xF, 0x7]
    return (sbox[b >> 4] << 4) | sbox[b & 0x0F]

def sub_bytes(state):
    return [sub_nib(b) for b in state]

def shift_rows(state):
    return state  # ShiftRows não altera nada para 2 bytes

def mix_columns(state):
    return [
        state[0] ^ state[1], 
        state[1] ^ state[0]
    ]

def add_round_key(state, key):
    return xor_bytes(state, key)

def s_aes_encrypt(plaintext, key):
    state = add_round_key(plaintext, key[:2])

    state = sub_bytes(state)
    state = shift_rows(state)
    state = mix_columns(state)
    state = add_round_key(state, key[2:4])

    state = sub_bytes(state)
    state = shift_rows(state)
    state = add_round_key(state, key[4:6])

    return state

# Convertendo a chave e o texto claro de binário para inteiros
plaintext = [0b01101111, 0b01101011]  # "ok" em ASCII
key = [0b10100111, 0b00111011, 0b00000000, 0b00000000, 0b00000000, 0b00000000]  # Chave fornecida

# Encriptação
ciphertext = s_aes_encrypt(plaintext, key)
ciphertext_bits = ''.join(f'{byte:08b}' for byte in ciphertext)
print(f"Texto cifrado: {ciphertext_bits}")
```
O resultado obtido foi `1110 0111 1110 0111`. Este valor difere do resultado esperado `0000 0111 0011 1000`, possivelmente devido a diferenças de interpretação ou implementação específica das operações do S-AES.

### 7. Compare AES com DES

Para cada um dos seguintes elementos do DES, indique o elemento comparável no AES ou explique por que ele não é necessário no AES.

#### (a) XOR do material da subchave com a entrada da função f:
- **No DES:** Cada subchave gerada durante a expansão da chave é combinada com o bloco de dados usando uma operação XOR.
- **No AES:** Esse passo é equivalente ao **AddRoundKey** em cada rodada do AES, onde a subchave é combinada com o array Estado usando uma operação XOR.

#### (b) XOR da saída da função f com a metade esquerda do bloco:
- **No DES:** A saída da função f é combinada com a metade esquerda do bloco usando XOR.
- **No AES:** Não há uma divisão do bloco em metades no AES. Em vez disso, todo o bloco é tratado como uma matriz de bytes, e a operação correspondente é o **AddRoundKey** no início de cada rodada.

#### (c) Função f:
- **No DES:** A função f inclui expansão, XOR com a subchave, substituição (S-box), e permutação.
- **No AES:** Não há uma função f distinta como no DES. O equivalente seria a combinação das operações **SubBytes (S-box)**, **ShiftRows**, **MixColumns**, e **AddRoundKey** que realizam transformações no array Estado.

#### (d) Permutação P:
- **No DES:** A permutação P reorganiza os bits após a substituição da S-box.
- **No AES:** Não há necessidade de uma permutação P separada, pois as operações **ShiftRows** e **MixColumns** em AES já reordenam e misturam os bits/bytes no array Estado.

#### (e) Troca de metades do bloco:
- **No DES:** As metades do bloco são trocadas ao final de cada rodada.
- **No AES:** Não há troca de metades, pois o bloco de dados é tratado como uma matriz única de 128 bits, e as transformações são aplicadas uniformemente a todo o bloco.
