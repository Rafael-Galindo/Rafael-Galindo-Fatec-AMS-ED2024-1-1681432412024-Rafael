# Análise de Desempenho de Algoritmos

**Equipe:**

- Rafael Willian Galindo Neto
- Murilo Grillo Bastos
- Giovanni Montteiro
- Vitor Tamais Fischer

Data: [**/**/****]


## Descrição de Negócio

O problema que abordaremos consiste em desenvolver uma solução computacional para simular o funcionamento de um sistema de gestão de filas em um restaurante, onde diferentes processos são gerenciados com base no estado de atendimento. A eficiência do atendimento será otimizada utilizando laços de repetição e recursividade, permitindo que o sistema escale adequadamente à medida que o número de pedidos cresce.


## Macro Solução

A solução envolve três laços de repetição para os seguintes processos:

1. **Fila de atendimento**: Um laço `while` que processa pedidos até que todos sejam atendidos.
2. **Consulta de menu**: Um laço `for` para iterar sobre os itens do menu, calculando o tempo de preparo de cada pedido.
3. **Verificação de estoque**: Um laço `do-while` que continua verificando os níveis de estoque até que seja possível preparar o próximo pedido.

Além disso, uma função recursiva será usada para calcular o tempo total de atendimento, levando em conta a recursividade para ajustar o tempo de espera de acordo com a complexidade dos pedidos.


## Ferramentas e Linguagens

- **Linguagem de Programação:** C (escolhida por seu desempenho e controle detalhado de memória).
- **Ferramentas:** GCC (GNU Compiler Collection) para compilar o código, e Github para controle de versão e colaboração.


Código em C:

#include <stdio.h>
#include <stdlib.h>
#include <time.h>

// Função recursiva para calcular o tempo total de espera
int calcular_tempo_total(int pedidos[], int n) {
    if (n == 0) {
        return 0; // Caso base: sem pedidos, tempo total é zero
    }
    // Tempo total é o tempo do pedido atual mais o tempo dos pedidos restantes
    return pedidos[n-1] + calcular_tempo_total(pedidos, n-1);
}

int main() {
    int pedidos[5]; // Armazena o tempo de preparo de 5 pedidos
    int estoque[5] = {5, 3, 4, 2, 6}; // Quantidade de itens em estoque
    int menu[5] = {10, 15, 20, 25, 30}; // Tempo de preparo de cada item no menu
    int i, j, total_tempo;
    int num_pedidos = 5; // Número de pedidos

    srand(time(0)); // Inicializa o gerador de números aleatórios

    // 1. Simulando o atendimento de pedidos em uma fila (laço while)
    printf("Processando fila de pedidos:\n");
    i = 0;
    while (i < num_pedidos) {
        pedidos[i] = menu[rand() % 5]; // Atribui tempos de preparo aleatórios do menu
        printf("Pedido %d: tempo de preparo = %d minutos\n", i + 1, pedidos[i]);
        i++;
    }

    // 2. Verificando o menu (laço for)
    printf("\nVerificando o menu:\n");
    for (j = 0; j < 5; j++) {
        printf("Item %d: tempo de preparo = %d minutos\n", j + 1, menu[j]);
    }

    // 3. Verificando estoque até que um item com estoque suficiente seja encontrado (laço do-while)
    printf("\nVerificando estoque para o próximo pedido:\n");
    int item = 0;
    do {
        printf("Verificando estoque do item %d... ", item + 1);
        if (estoque[item] > 0) {
            printf("Item disponível! Processando pedido...\n");
        } else {
            printf("Estoque esgotado. Verificando próximo item.\n");
        }
        item++;
    } while (item < 5 && estoque[item - 1] == 0);

    // 4. Calculando o tempo total de preparo usando recursividade
    total_tempo = calcular_tempo_total(pedidos, num_pedidos);
    printf("\nTempo total de preparo dos pedidos: %d minutos\n", total_tempo);

    return 0;
}



Explicação do Código:
Laço de repetição while:

1.Processa uma fila de 5 pedidos, onde os tempos de preparo são atribuídos aleatoriamente com base no menu.

2.Laço de repetição for:
Exibe o tempo de preparo de cada item do menu.

3.Laço de repetição do-while:
Verifica o estoque dos itens. Continua até encontrar um item com estoque disponível.

4.Função recursiva calcular_tempo_total:
Calcula o tempo total de preparo somando o tempo de cada pedido de forma recursiva.

Saída Exemplo:

Processando fila de pedidos:
Pedido 1: tempo de preparo = 30 minutos
Pedido 2: tempo de preparo = 20 minutos
Pedido 3: tempo de preparo = 25 minutos
Pedido 4: tempo de preparo = 15 minutos
Pedido 5: tempo de preparo = 10 minutos

Verificando o menu:
Item 1: tempo de preparo = 10 minutos
Item 2: tempo de preparo = 15 minutos
Item 3: tempo de preparo = 20 minutos
Item 4: tempo de preparo = 25 minutos
Item 5: tempo de preparo = 30 minutos

Verificando estoque para o próximo pedido:
Verificando estoque do item 1... Item disponível! Processando pedido...

Tempo total de preparo dos pedidos: 100 minutos

