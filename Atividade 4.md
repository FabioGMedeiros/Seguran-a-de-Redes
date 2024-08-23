# Atividade Cap. 04 - Conceitos básicos de Teoria dos Números e Corpos Finitos

## 1. Definições

- **Grupo**: Um grupo é um conjunto \( G \) com uma operação binária \( * \) que combina dois elementos para formar outro elemento do mesmo conjunto, satisfazendo quatro axiomas: fechamento, associatividade, existência de elemento neutro e existência de elementos inversos.

- **Anel**: Um anel é um conjunto \( R \) equipado com duas operações binárias (geralmente adição e multiplicação) que satisfazem as propriedades: é um grupo abeliano sob adição, é fechado sob multiplicação, a multiplicação é associativa e a multiplicação é distributiva em relação à adição.

- **Corpo**: Um corpo é um anel com unidade \( 1 \neq 0 \) no qual cada elemento não nulo possui um inverso multiplicativo. Além disso, a multiplicação é comutativa.

## 2. Divisores

Dizer que \( b \) é um divisor de \( a \) significa que existe um inteiro \( k \) tal que \( a = b \cdot k \). Em outras palavras, \( b \) divide \( a \) sem deixar resto.

## 3. Encontrar \( x \) que satisfaça as equações

1. Para 5x ≡ 4 (mod 3):

   5 ≡ 2 (mod 3), então 2x ≡ 4 (mod 3)

   Dividindo ambos os lados por 2:

   x ≡ 2 (mod 3)

   Portanto, x = 2.

2. Para 7x ≡ 6 (mod 5):

   7 ≡ 2 (mod 5), então 2x ≡ 6 (mod 5)

   Simplificando 6 ≡ 1 (mod 5):

   2x ≡ 1 (mod 5)

   O inverso multiplicativo de 2 módulo 5 é 3, então multiplicando ambos os lados por 3:

   x ≡ 3 (mod 5)

   Portanto, x = 3.

3. Para 9x ≡ 8 (mod 7):

   9 ≡ 2 (mod 7), então 2x ≡ 8 (mod 7)

   Simplificando 8 ≡ 1 (mod 7):

   2x ≡ 1 (mod 7)

   O inverso multiplicativo de 2 módulo 7 é 4, então multiplicando ambos os lados por 4:

   x ≡ 4 (mod 7)

   Portanto, x = 4.

## 4. Inversos multiplicativos em \( \mathbb{Z}_5 \)

Os elementos não nulos em \( \mathbb{Z}_5 \) são {1, 2, 3, 4}:

- 1^(-1) ≡ 1 (mod 5)
- 2^(-1) ≡ 3 (mod 5) porque 2 × 3 = 6 ≡ 1 (mod 5)
- 3^(-1) ≡ 2 (mod 5) porque 3 × 2 = 6 ≡ 1 (mod 5)
- 4^(-1) ≡ 4 (mod 5) porque 4 × 4 = 16 ≡ 1 (mod 5)

## 5. Máximo divisor comum (MDC)

1. Para mdc(24140, 16762):

   24140 = 16762 × 1 + 738

   16762 = 738 × 22 + 526

   738 = 526 × 1 + 212

   526 = 212 × 2 + 102

   212 = 102 × 2 + 8

   102 = 8 × 12 + 6

   8 = 6 × 1 + 2

   6 = 2 × 3 + 0

   Portanto, o MDC é 2.

2. Para mdc(4655, 12075):

   12075 = 4655 × 2 + 2765

   4655 = 2765 × 1 + 1890

   2765 = 1890 × 1 + 875

   1890 = 875 × 2 + 140

   875 = 140 × 6 + 35

   140 = 35 × 4 + 0

   Portanto, o MDC é 35.

## 6. Algoritmo de Euclides estendido

1. Para 1234 mod 4321:

   Usando o algoritmo de Euclides estendido, encontramos:

   1234^(-1) ≡ 2640 (mod 4321)

2. Para 24140 mod 40902:

   O MDC é 2, então 24140 não tem inverso multiplicativo mod 40902.

3. Para 550 mod 1769:

   Usando o algoritmo de Euclides estendido, encontramos:

   550^(-1) ≡ 567 (mod 1769)

## 7. Inverso multiplicativo de x³ + x + 1 em GF(2⁴)

Para encontrar o inverso multiplicativo, usamos a aritmética de polinômios mod m(x) = x⁴ + x + 1:

(x³ + x + 1) × (a₃x³ + a₂x² + a₁x + a₀) ≡ 1 (mod x⁴ + x + 1)

## 8. Aritmética de polinômios em \( \mathbb{Z}_{10} \)

1. Para (7x + 2) - (x² + 5):

   (7x + 2) - (x² + 5) = -x² + 7x + (2 - 5) = -x² + 7x - 3 ≡ -x² + 7x + 7 (mod 10)

2. Para (6x² + x + 3) × (5x² + 2):

   (6x² + x + 3) × (5x² + 2)

   = 6x² × 5x² + 6x² × 2 + x × 5x² + x × 2 + 3 × 5x² + 3 × 2

   = 30x⁴ + 12x² + 5x³ + 2x + 15x² + 6

   = 30x⁴ + 5x³ + 27x² + 2x + 6

   Como x⁴ ≡ -x (mod 10):

   30x⁴ ≡ -30x ≡ 0 (mod 10)

   Portanto:

   = 5x³ + 27x² + 2x + 6

## 9. Calculadora Simples de Quatro Funções em GF(2⁴)

Para criar uma calculadora simples que realiza as quatro operações básicas em GF(2⁴), precisamos representar cada elemento de GF(2⁴) como um polinômio de grau menor que 4 e realizar as operações com aritmética de polinômios mod x⁴ + x + 1.

1. **Adição**: Soma-se coeficiente por coeficiente, sem acarreamento.
2. **Subtração**: Igual à adição em GF(2⁴).
3. **Multiplicação**: Multiplica-se os polinômios e reduz-se módulo x⁴ + x + 1.
4. **Divisão**: Multiplica-se pelo inverso multiplicativo do divisor.

Exemplo de multiplicação: (x³ + x + 1) × (x² + x) em GF(2⁴).
