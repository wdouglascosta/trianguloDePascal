# Programação Dinâmica
 ## Triângulo de Pascal - PAA
 
 
## *William Douglas - RA 89239*
## *André Luan - RA 90857*

### Descrição do Programa

```java
public static void main(String[] args) {

        int n = 25; // n define a altura da pirâmide, ou seja, a entrada do algoritmo
        Integer[][] triangulo = new Integer[n][n];

        for (int i = 0; i < n; i++) {
            for (int j = 0; j < i; j++) {
                    triangulo[i][j] = 0; // preenche de 0's as posições abaixo da linha diagonal principal
            }
            triangulo[i][0] = 1; // preenche a primeira coluna de 1's
            triangulo[i][i] = 1; // preenche de 1's a diagonal média da matriz
        }

        for (int i = 1; i < n; i++) { // percorre todas as linhas da matriz
            for (int j = 1; j < i; j++) { // este "for" percorre somente a parte abaixo da diagonal média da matriz
                    if (triangulo[i][j] == 0) {
                        int a = triangulo[i - 1][j - 1]; // a recebe o valor da coluna anterior e linha acima
                        int b = triangulo[i - 1][j]; // b recebe o valor da linha acima
                        triangulo[i][j] = a + b;
                }
            }
        }
        imprime(triangulo); // faz a impressão da matriz no console
    }

    public static void imprime(Integer[][] vetor) {

        int n = vetor.length;
        Integer a = n / 2;
        Integer maiorNumero = vetor[n - 1][a];
        int espacos = String.valueOf(maiorNumero).length();

        for (int i = 0; i < n; i++) {
            for (int k = 0; k < n - i; k++) {
                System.out.print("  ");
            }
            for (int j = 0; j < n; j++) {
                if (i < j) {
                    System.out.print("  ");
                } else {

                    System.out.print("  " + vetor[i][j]);
                }
            }

            System.out.println(" ");
        }
    }

```

O trecho principal do algoritmo:
```java 
        for (int i = 1; i < n; i++) { // percorre todas as linhas da matriz
            for (int j = 1; j < i; j++) { // este "for" percorre somente a parte abaixo da diagonal média da matriz
                    if (triangulo[i][j] == 0) {
                        int a = triangulo[i - 1][j - 1]; // a recebe o valor da coluna anterior e linha acima
                        int b = triangulo[i - 1][j]; // b recebe o valor da linha acima
                        triangulo[i][j] = a + b;
                }
            }
        }
```
possui dois ciclos "for" aninhados, o primeiro com i começando em 1 indo até n e o segundo com j indo de 1 até i, assim, tem-se que a complexidade do algoritmo é n*n/2 = O(n²).
