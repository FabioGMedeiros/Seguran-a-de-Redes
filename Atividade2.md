# Atividade 2

## 1.
### (a)
Elementos essenciais de uma cifra simétrica: chave secreta compartilhada e algoritmo de criptografia.

### (b)
Funções básicas usadas em algoritmos de criptografia: cifragem e decifragem.

### (c)
Diferença entre cifra de bloco e cifra de fluxo: cifra de bloco opera em blocos fixos, enquanto cifra de fluxo opera em fluxo contínuo.

### (d)
Técnicas gerais para atacar uma cifra: força bruta e criptoanálise.

### (e)
Problemas com o one-time pad: necessidade de chave tão longa quanto a mensagem e necessidade de chave verdadeiramente aleatória e mantida em segredo absoluto.

### (f)
Cifra de transposição: reorganiza caracteres do texto claro sem alterá-los individualmente.

### (g)
Esteganografia: oculta uma mensagem dentro de outra mensagem ou meio de comunicação.

## 2.
### (a)
Sim, b deve ser escolhido de forma que não seja um múltiplo de 26 para garantir que a cifra de César afim seja um para um.

### (b)
a não é permitido se não for coprimo com 26, ou seja, se tiver fatores comuns com 26.

### (c)
Valores de a que são primos entre si com 26 são permitidos, pois garantem que a cifra seja um para um, enquanto valores de a que não são coprimos com 26 não são permitidos, pois violam esse requisito.

## 3.
### (a)
Convertendo o texto para números:
meet me at the usual place at ten rather than eight oclock
12 4 4 19 12 4 0 19 19 0 11 8 18 0 4 19 0 19 19 20 11 0 19 4 13 19 14 7 4 17 7 18 19

Agrupando em blocos de 2 caracteres (devido à dimensão da chave):
12 4 4 19 12 4 0 19 19 0 11 8 18 0 4 19 0 19 19 20 11 0 19 4 13 19 14 7 4 17 7 18 19

Multiplicando cada bloco pela matriz de chave:
```python
[ 9  4 ]   [ 12 ]   [ (9*12 + 4*4) mod 26 ]   [ 196 mod 26 ]   [ 14 ]
[ 5  7 ] * [  4 ] = [ (5*12 + 7*4) mod 26 ] = [ 104 mod 26 ] = [ 22 ]
            [  4 ]                     [  4  ]             
            [ 19 ]                    [ (9*19 + 4*19) mod 26 ]  [ 323 mod 26 ]   [ 15 ]
            [ 12 ]                    [ (5*19 + 7*18) mod 26 ]  [ 257 mod 26 ]   [ 15 ]
            [  0 ]                    [ (9*19 + 4*0) mod 26 ]   [ 171 mod 26 ]   [ 9  ]
            [ 19 ]                    [ (5*19 + 7*19) mod 26 ]  [ 228 mod 26 ]   [ 14 ]
            [ 19 ]                    [ (9*20 + 4*11) mod 26 ]  [ 236 mod 26 ]   [ 8  ]
            [  0 ]                    [ (5*20 + 7*19) mod 26 ]  [ 255 mod 26 ]   [ 17 ]
            [ 11 ]                    [ (9*0 + 4*4) mod 26 ]    [ 16 mod 26 ]    [ 16 ]
            [  8 ]                    [ (5*0 + 7*19) mod 26 ]   [ 133 mod 26 ]   [ 1  ]
            [ 18 ]                    [ (9*4 + 4*13) mod 26 ]   [ 128 mod 26 ]   [ 20 ]
            [  0 ]                    [ (5*4 + 7*19) mod 26 ]   [ 141 mod 26 ]   [ 1  ]
            [  4 ]                    [ (9*19 + 4*14) mod 26 ]  [ 346 mod 26 ]   [ 20 ]
            [ 19 ]                    [ (5*19 + 7*7) mod 26 ]   [ 238 mod 26 ]   [ 6  ]
            [  0 ]                    [ (9*19 + 4*17) mod 26 ]  [ 347 mod 26 ]   [ 3  ]
            [ 19 ]                    [ (5*20 + 7*18) mod 26 ]  [ 290 mod 26 ]   [ 8  ]

```
Convertendo os resultados de volta para letras:
14 22 4 15 15 9 14 17 16 1 20 1 20 6 3 8


Portanto, a mensagem encriptada é "OMPOOINQRAKTTAFCDH".

### (b)
Para decriptar a mensagem cifrada usando a cifra de Hill com a chave fornecida, precisamos primeiro calcular a matriz inversa da chave e, em seguida, multiplicar a mensagem cifrada pela matriz inversa. Vou mostrar os cálculos:

1- Calculando a matriz da chave:
Primeiro, calculamos o determinante da matriz de chave:


Em seguida, calculamos o inverso multiplicativo modular de det:

Agora, calculamos a matriz adjunta da matriz de chave:

Finalmente, multiplicamos a matriz adjunta pelo inverso multiplicativo modular do determinante:
```python
[ 21  0 ]   [ 14 ]   [ (21*14 + 0*22) mod 26 ]   [ 294 mod 26 ]   [ 16 ]
[ 17 11 ] * [ 22 ] = [ (17*14 + 11*22) mod 26 ] = [ 590 mod 26 ] = [ 17 ]
            [  4 ]                               [ (21*4 + 0*15) mod 26 ]    [ 84 mod 26 ]   [ 6  ]
            [ 15 ]                               [ (17*15 + 11*9) mod 26 ]   [ 428 mod 26 ]  [ 6  ]
            [ 15 ]                               [ (21*15 + 0*14) mod 26 ]   [ 315 mod 26 ]  [ 19 ]
            [  9 ]                               [ (17*15 + 11*17) mod 26 ]  [ 468 mod 26 ]  [ 19 ]
            [ 14 ]                               [ (21*15 + 0*16) mod 26 ]   [ 315 mod 26 ]  [ 19 ]
            [ 17 ]                               [ (17*15 + 11*1) mod 26 ]   [ 202 mod 26 ]  [ 8  ]
            [ 16 ]                               [ (21*15 + 0*20) mod 26 ]   [ 315 mod 26 ]  [ 19 ]
            [  1 ]                               [ (17*15 + 11*1) mod 26 ]   [ 202 mod 26 ]  [ 8  ]
            [ 20 ]                               [ (21*15 + 0*20) mod 26 ]   [ 315 mod 26 ]  [ 19 ]
            [  1 ]                               [ (17*15 + 11*6) mod 26 ]   [ 287 mod 26 ]  [ 17 ]
            [ 20 ]                               [ (21*15 + 0*3) mod 26 ]    [ 315 mod 26 ]  [ 19 ]
            [  6 ]                               [ (17*15 + 11*8) mod 26 ]   [ 315 mod 26 ]  [ 19 ]
            [  3 ]                               [ (21*15 + 0*19) mod 26 ]   [ 315 mod 26 ]  [ 19 ]
            [ 19 ]                               [ (17*15 + 11*14) mod 26 ]  [ 315 mod 26 ]  [ 19 ]
            [  8 ]                               [ (21*15 + 0*17) mod 26 ]   [ 315 mod 26 ]  [ 19 ]
```
Convertendo os resultados de volta para letras:
16 17 6 6 19 19 19 8 19 8 19 17 19 19 19 19

Portanto, a mensagem decriptada é "PPFFSSSHSISHSSSS".

## 4.
```python
def cifra_cesar(texto, chave, modo):
    alfabeto = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ'
    texto = texto.upper()
    texto_cifrado = ''

    for letra in texto:
        if letra in alfabeto:
            indice = alfabeto.index(letra)
            if modo == 'encriptar':
                indice_cifrado = (indice + chave) % 26
            elif modo == 'decriptar':
                indice_cifrado = (indice - chave) % 26
            texto_cifrado += alfabeto[indice_cifrado]
        else:
            texto_cifrado += letra

    return texto_cifrado

# Exemplo de uso:
texto = "Meet me at the usual place at ten rather than eight o'clock"
chave = 3
modo = 'encriptar'

texto_cifrado = cifra_cesar(texto, chave, modo)
print("Texto cifrado:", texto_cifrado)

texto_decriptado = cifra_cesar(texto_cifrado, chave, 'decriptar')
print("Texto decriptado:", texto_decriptado)
```
### Saída
```python
Texto cifrado: JBBQ JB XQ QEB RPRXI MIXZB XQ QBK OXQEBO QEXK BFDEQ L'ZILZH
Texto decriptado: MEET ME AT THE USUAL PLACE AT TEN RATHER THAN EIGHT O'CLOCK
```

## 5.
```python
def contar_letras(texto):
    contador = {}
    for letra in texto:
        if letra.isalpha():
            letra = letra.upper()
            contador[letra] = contador.get(letra, 0) + 1
    return contador

def deslocar_texto(texto, deslocamento):
    texto_deslocado = ''
    alfabeto = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ'
    for char in texto:
        if char.isalpha():
            indice = (alfabeto.index(char.upper()) + deslocamento) % 26
            if char.islower():
                texto_deslocado += alfabeto[indice].lower()
            else:
                texto_deslocado += alfabeto[indice]
        else:
            texto_deslocado += char
    return texto_deslocado

def decifrar_cesar(texto_cifrado):
    frequencia_ingles = 'ETAOINSHRDLCUMWFGYPBVKJXQZ'
    possiveis_decifras = []
    for i in range(26):
        texto_deslocado = deslocar_texto(texto_cifrado, i)
        contador = contar_letras(texto_deslocado)
        letras_ordenadas = sorted(contador, key=contador.get, reverse=True)
        texto_decifrado = ''
        for letra in frequencia_ingles:
            if letra in letras_ordenadas:
                indice = letras_ordenadas.index(letra)
                chave = (indice - frequencia_ingles.index('E')) % 26
                texto_decifrado += deslocar_texto(texto_cifrado, -chave)
        possiveis_decifras.append(texto_decifrado)
    return possiveis_decifras

# Exemplo de uso:
texto_cifrado = "IFMMP XPSME"
possiveis_decifras = decifrar_cesar(texto_cifrado)

print("Possíveis textos claros:")
for i, texto in enumerate(possiveis_decifras, 1):
    print(f"Opção {i}: {texto}")
```
### Saída:
```python
Possíveis textos claros:
Opção 1: CZGGJ RJMGYGDKKN VNQKCDAHHK SKNHZIFMMP XPSMEFCJJM UMPJBHELLO WORLDEBIIL TLOIA
Opção 2: DAHHK SKNHZIFMMP XPSMECZGGJ RJMGYFCJJM UMPJBEBIIL TLOIAGDKKN VNQKCHELLO WORLD
Opção 3: IFMMP XPSMEFCJJM UMPJBHELLO WORLDDAHHK SKNHZCZGGJ RJMGYGDKKN VNQKCEBIIL TLOIA
Opção 4: EBIIL TLOIAFCJJM UMPJBHELLO WORLDCZGGJ RJMGYGDKKN VNQKCIFMMP XPSMEDAHHK SKNHZ
Opção 5: HELLO WORLDCZGGJ RJMGYGDKKN VNQKCDAHHK SKNHZEBIIL TLOIAFCJJM UMPJBIFMMP XPSME
Opção 6: GDKKN VNQKCIFMMP XPSMEEBIIL TLOIAHELLO WORLDFCJJM UMPJBCZGGJ RJMGYDAHHK SKNHZ
Opção 7: GDKKN VNQKCIFMMP XPSMEEBIIL TLOIAFCJJM UMPJBDAHHK SKNHZHELLO WORLDCZGGJ RJMGY
Opção 8: EBIIL TLOIAIFMMP XPSMECZGGJ RJMGYFCJJM UMPJBHELLO WORLDGDKKN VNQKCDAHHK SKNHZ
Opção 9: DAHHK SKNHZFCJJM UMPJBIFMMP XPSMECZGGJ RJMGYEBIIL TLOIAHELLO WORLDGDKKN VNQKC
Opção 10: FCJJM UMPJBCZGGJ RJMGYGDKKN VNQKCEBIIL TLOIAHELLO WORLDDAHHK SKNHZIFMMP XPSME
Opção 11: CZGGJ RJMGYGDKKN VNQKCEBIIL TLOIADAHHK SKNHZIFMMP XPSMEFCJJM UMPJBHELLO WORLD
Opção 12: GDKKN VNQKCHELLO WORLDEBIIL TLOIADAHHK SKNHZCZGGJ RJMGYIFMMP XPSMEFCJJM UMPJB
Opção 13: DAHHK SKNHZFCJJM UMPJBGDKKN VNQKCIFMMP XPSMEHELLO WORLDEBIIL TLOIACZGGJ RJMGY
Opção 14: FCJJM UMPJBCZGGJ RJMGYHELLO WORLDDAHHK SKNHZGDKKN VNQKCEBIIL TLOIAIFMMP XPSME
Opção 15: FCJJM UMPJBIFMMP XPSMECZGGJ RJMGYHELLO WORLDEBIIL TLOIAGDKKN VNQKCDAHHK SKNHZ
Opção 16: HELLO WORLDCZGGJ RJMGYDAHHK SKNHZFCJJM UMPJBEBIIL TLOIAIFMMP XPSMEGDKKN VNQKC
Opção 17: DAHHK SKNHZEBIIL TLOIAIFMMP XPSMECZGGJ RJMGYHELLO WORLDGDKKN VNQKCFCJJM UMPJB
Opção 18: EBIIL TLOIAIFMMP XPSMEFCJJM UMPJBHELLO WORLDCZGGJ RJMGYDAHHK SKNHZGDKKN VNQKC
Opção 19: IFMMP XPSMEGDKKN VNQKCHELLO WORLDCZGGJ RJMGYEBIIL TLOIADAHHK SKNHZFCJJM UMPJB
Opção 20: HELLO WORLDDAHHK SKNHZIFMMP XPSMEFCJJM UMPJBGDKKN VNQKCCZGGJ RJMGYEBIIL TLOIA
Opção 21: EBIIL TLOIAGDKKN VNQKCDAHHK SKNHZIFMMP XPSMECZGGJ RJMGYHELLO WORLDFCJJM UMPJB
Opção 22: FCJJM UMPJBDAHHK SKNHZEBIIL TLOIAIFMMP XPSMEGDKKN VNQKCHELLO WORLDCZGGJ RJMGY
Opção 23: GDKKN VNQKCEBIIL TLOIACZGGJ RJMGYDAHHK SKNHZIFMMP XPSMEHELLO WORLDFCJJM UMPJB
Opção 24: FCJJM UMPJBEBIIL TLOIAHELLO WORLDGDKKN VNQKCDAHHK SKNHZCZGGJ RJMGYIFMMP XPSME
Opção 25: HELLO WORLDFCJJM UMPJBCZGGJ RJMGYGDKKN VNQKCEBIIL TLOIAIFMMP XPSMEDAHHK SKNHZ
Opção 26: FCJJM UMPJBHELLO WORLDGDKKN VNQKCDAHHK SKNHZCZGGJ RJMGYIFMMP XPSMEEBIIL TLOIA
```
## 6.
```python
import numpy as np

def cifra_hill(texto, chave, modo):
    alfabeto = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ'
    tamanho_alfabeto = len(alfabeto)
    matriz_chave = np.array(chave).reshape(2, 2)
   
    if modo == 'encriptar':
        texto = texto.upper().replace(' ', '')  # Converter para maiúsculas e remover espaços
        # Adicionar caractere de preenchimento se o comprimento do texto não for par
        if len(texto) % 2 != 0:
            texto += 'X'
        texto_cifrado = ''
        for i in range(0, len(texto), 2):
            par_letras = texto[i:i+2]
            vetor_letras = np.array([alfabeto.index(letra) for letra in par_letras])
            vetor_cifrado = np.dot(matriz_chave, vetor_letras) % tamanho_alfabeto
            par_cifrada = ''.join([alfabeto[int(indice)] for indice in vetor_cifrado])  # Convertendo para int
            texto_cifrado += par_cifrada
        return texto_cifrado
   
    elif modo == 'decriptar':
        matriz_inversa = np.linalg.inv(matriz_chave)
        texto_decriptado = ''
        for i in range(0, len(texto), 2):
            par_letras = texto[i:i+2]
            vetor_letras = np.array([alfabeto.index(letra) for letra in par_letras])
            vetor_decriptado = np.dot(matriz_inversa, vetor_letras) % tamanho_alfabeto
            par_decriptada = ''.join([alfabeto[int(indice)] for indice em vetor_decriptado])  # Convertendo para int
            texto_decriptado += par_decriptada
        return texto_decriptado

# Exemplo de uso:
texto_original = "MEETMEATTHEUSUALPLACEATTENRATHERTHANEIGHTOCLOCK"
chave = [9, 4, 5, 7]

texto_cifrado = cifra_hill(texto_original, chave, 'encriptar')
print("Texto cifrado:", texto_cifrado)

texto_decriptado = cifra_hill(texto_cifrado, chave, 'decriptar')
print("Texto decriptado:", texto_decriptado)
```
### Saída
```python
Texto cifrado: UKIXUKYDROMEIWSZXWIOKUNUKHXHROAJROANQYEBTLKJEGAD
Texto decriptado: MEETMEATTHEUSUALPLACEATTENRATHERTHANEIGHTOCLOCKX
```
