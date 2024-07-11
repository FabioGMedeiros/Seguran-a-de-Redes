# Questionamentos

## 1. Responda os questionamentos a seguir:

(a) **Por que é importante estudar a cifra de Feistel?**

A cifra de Feistel é fundamental no campo da criptografia porque serve como base para muitos algoritmos de cifra de bloco, incluindo o DES (Data Encryption Standard). A sua estrutura permite a criação de algoritmos de criptografia seguros e eficientes que são resistentes a vários tipos de ataques criptográficos. A cifra de Feistel é importante porque equilibra segurança e desempenho, utilizando uma combinação de operações simples para garantir a segurança dos dados.

(b) **Qual é a diferença entre uma cifra de bloco e uma cifra de fluxo?**

- **Cifra de bloco:** Opera em blocos fixos de bits ou caracteres, criptografando um bloco inteiro de dados de cada vez. Exemplos incluem DES e AES.
- **Cifra de fluxo:** Criptografa dados um bit ou byte de cada vez, gerando um fluxo de chave que é combinado com o texto claro usando operações como XOR. Exemplos incluem RC4.

(c) **Por que não é prático usar uma cifra de substituição reversível qualquer do tipo mostrado na Tabela 3.1?**

Uma cifra de substituição simples não é prática porque é vulnerável a análises estatísticas e criptoanálises. Com técnicas como a análise de frequência, um atacante pode facilmente deduzir o texto original, especialmente se o texto cifrado for suficientemente longo.

(d) **O que é uma cifra de produto?**

Uma cifra de produto combina duas ou mais operações criptográficas simples, como substituição e transposição, para criar uma cifra mais complexa e segura. Um exemplo clássico é a cifra de Feistel, que aplica várias rodadas de operações para aumentar a segurança.

(e) **Qual é a diferença entre difusão e confusão?**

- **Difusão:** Refere-se ao espalhamento do impacto de um único bit de texto claro sobre muitos bits de texto cifrado, tornando mais difícil inferir a estrutura do texto claro.
- **Confusão:** Refere-se a complicar a relação entre a chave de criptografia e o texto cifrado, dificultando a dedução da chave.

(f) **Que parâmetros e escolhas de projeto determinam o algoritmo real de uma cifra de Feistel?**

- Tamanho do bloco de dados.
- Tamanho da chave de criptografia.
- Número de rodadas de processamento.
- Estrutura da função da rodada (função F).
- Algoritmo de geração de sub-chaves.
- Esquema de permutação e substituição usado.

(g) **Explique o efeito avalanche.**

O efeito avalanche é uma propriedade desejável de algoritmos criptográficos onde uma pequena alteração no texto claro ou na chave de criptografia resulta em uma grande mudança no texto cifrado. Isso garante que pequenas variações nos dados de entrada produzem saídas significativamente diferentes, dificultando a análise e a previsão do algoritmo.

## 2. Qual(is) dos recursos abaixo estão presentes no projeto da rede de Feistel? Explique.

(a) **Tamanho do bloco e da chave:** Sim, o tamanho do bloco e da chave são essenciais no design de uma cifra de Feistel, pois determinam a quantidade de dados processados e a segurança do algoritmo.

(b) **Função da rodada:** Sim, a função da rodada é um componente crítico na cifra de Feistel, responsável por introduzir confusão e difusão em cada rodada do processo de criptografia.

(c) **Gerador de sub-chaves:** Sim, um gerador de sub-chaves é necessário para derivar chaves específicas para cada rodada a partir da chave principal, adicionando complexidade e segurança ao algoritmo.

(d) **Todas as alternativas:** Sim, todos esses recursos são fundamentais no projeto da rede de Feistel.

## 3. Qual é o tamanho do texto claro no Data Encryption Standard (DES)? Explique.

(a) 57;
(b) 48;
(c) 32;
(d) **64**.

O tamanho do texto claro no DES é 64 bits. Isso significa que o DES processa dados em blocos de 64 bits, aplicando operações de substituição e permutação para criptografar cada bloco de dados.

## 4. A cifra de Feistel do algoritmo de encriptação utilizada no Data Encryption Standard (DES) utiliza quantos S-boxes? Explique.

(a) **8**;
(b) 7;
(c) 6;
(d) 5.

O DES utiliza 8 S-boxes (Substitution boxes). Cada S-box pega um bloco de 6 bits como entrada e o transforma em um bloco de 4 bits como saída. As S-boxes são usadas para introduzir não-linearidade no processo de criptografia, aumentando a complexidade e segurança do algoritmo.

## 5. O Data Encryption Standard possui uma chave de 56 bits, o que torna possível um espaço de 2^56 chaves possíveis. Essa sentença trata de ataque de... Explique.

(a) Tempo;
(b) Matemático;
(c) **Força-Bruta**;
(d) DoS.

A sentença refere-se a um ataque de força-bruta. Esse tipo de ataque envolve tentar todas as chaves possíveis até encontrar a correta. Com uma chave de 56 bits, há 2^56 possíveis chaves que um atacante precisaria testar para decifrar o texto cifrado, tornando a tarefa computacionalmente intensiva, mas factível com recursos suficientes.

# Questão 6: Cifragem e Decifragem de 16 Bits em 2 Rounds

## Descrição

Demonstre, através de um exemplo, como realizar a cifragem de 16 bits (dois caracteres), em 2 rounds. Em seguida, decifre o texto cifrado. Explique o processo passo a passo.

## Solução

### Passo a Passo da Cifragem e Decifragem

1. **Função de Round (`f`)**:
   - Utiliza-se uma função simples `f(x, k) = x XOR k`.

2. **Divisão da Mensagem**:
   - A mensagem de 2 caracteres é dividida em dois blocos de 8 bits cada (`L0` e `R0`).

3. **Cifragem em 2 Rounds**:
   - No primeiro round, aplica-se a função de round ao bloco direito `R0` com a chave `K1` e combina-se com o bloco esquerdo `L0`.
   - No segundo round, repete-se o processo com a chave `K2`.

4. **Decifragem**:
   - A decifragem inverte os passos da cifragem utilizando as chaves na ordem inversa (`K2` e `K1`).

### Código Python

```python
def f(x, k):
    return x ^ k

def feistel_encrypt(L0, R0, K1, K2):
    # Round 1
    L1 = R0
    R1 = L0 ^ f(R0, K1)
    # Round 2
    L2 = R1
    R2 = L1 ^ f(R1, K2)
    return (L2, R2)

def feistel_decrypt(L2, R2, K1, K2):
    # Inverse Round 2
    R1 = L2
    L1 = R2 ^ f(R1, K2)
    # Inverse Round 1
    R0 = L1
    L0 = R1 ^ f(R0, K1)
    return (L0, R0)

def bits_to_text(bits):
    """Convert 16-bit binary to ASCII text (2 characters)"""
    char1 = chr((bits >> 8) & 0xFF)
    char2 = chr(bits & 0xFF)
    return char1 + char2

def text_to_bits(text):
    """Convert 2-character ASCII text to 16-bit binary"""
    if len(text) != 2:
        raise ValueError("Input text must be exactly 2 characters long")
    return (ord(text[0]) << 8) | ord(text[1])

# Exemplo de uso
message = "Hi"  # 2-character ASCII text
if len(message) != 2:
    raise ValueError("A mensagem deve ter exatamente 2 caracteres")

L0 = ord(message[0])
R0 = ord(message[1])

K1 = 0b10101010
K2 = 0b01010101

# Cifragem
L2, R2 = feistel_encrypt(L0, R0, K1, K2)
ciphertext = (L2 << 8) | R2
ciphertext_text = bits_to_text(ciphertext)

print(f"Texto cifrado (binário): {ciphertext:016b}")
print(f"Texto cifrado (texto): {ciphertext_text}")

# Decifragem
L0_dec, R0_dec = feistel_decrypt(L2, R2, K1, K2)
plaintext = (L0_dec << 8) | R0_dec
plaintext_text = bits_to_text(plaintext)

print(f"Texto decifrado (binário): {plaintext:016b}")
print(f"Texto decifrado (texto): {plaintext_text}")
```

### Saída
```python
Texto cifrado (binário): 1000101110110111
Texto cifrado (texto): ·
Texto decifrado (binário): 0100100001101001
Texto decifrado (texto): Hi
```

## 7. Considere uma cifra de Feistel composta de 16 rodadas com tamanho de bloco de 128 bits e tamanho de chave de 128 bits. Suponha que, para determinado k, o algoritmo de escalonamento de chave defina valores as oito primeiras chaves de rodada, k1, k2, . . . , k8, e depois estabeleça k9 = k8, k10 = k7, k11 = k6, . . . , k16 = k1. Admita que você tenha um texto cifrado S. Explique como, com acesso a um oráculo de encriptação, você pode decriptar c e determinar m usando apenas uma única consulta a ele. Isso mostra que tal cifra é vulnerável a um ataque de texto claro escolhido.

# Ataque de Texto Claro Escolhido em uma Cifra de Feistel com Chaves Repetidas

## Resumo do Ataque

1. **Escolha um Texto Claro \( M \)**: Escolha um texto claro aleatório \( M \) e divida-o em duas metades \( L_0 \) e \( R_0 \).

2. **Obtenha o Texto Cifrado \( C \)**: Use o oráculo de encriptação para cifrar \( M \), resultando em \( C = (L_{16}, R_{16}) \).

3. **Decripte o Texto Cifrado \( S \)**: Forneça \( S \) ao oráculo de encriptação como se fosse um texto claro. Devido à repetição das chaves de rodada (k9 = k8, k10 = k7, ..., k16 = k1), a encriptação de \( S \) pelo oráculo retornará o texto claro original \( M \).

## Conclusão

Com apenas uma consulta ao oráculo de encriptação com um texto claro escolhido, é possível decriptar qualquer texto cifrado (S) fornecido posteriormente, mostrando que a cifra é vulnerável a um ataque de texto claro escolhido.
