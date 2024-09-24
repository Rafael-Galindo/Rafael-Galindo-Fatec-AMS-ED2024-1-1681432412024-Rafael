# Análise de Desempenho de Algoritmos

**Equipe:**

- Rafael Willian Galindo Neto
- Murilo Grillo Bastos
- Giovanni Montteiro
- Vitor Tamais Fischer

Data: [##-##-####]


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

// Função recursiva para calcular o tempo total de preparo dos pedidos
int calcular_tempo_total(int pedidos[], int n) {

    // Caso base: se não houver pedidos, o tempo total é zero
    if (n == 0) {
        return 0;
    }
    
    // Recursivamente soma o tempo do último pedido ao total dos anteriores
    return pedidos[n - 1] + calcular_tempo_total(pedidos, n - 1);
}

// Função para verificar estoque de forma iterativa
int verificar_estoque(int estoque[], int tamanho) {
    int item = 0;
    
    // Itera sobre o estoque para encontrar um item disponível
    while (item < tamanho) {
        printf("Verificando estoque do item %d... ", item + 1);
        if (estoque[item] > 0) {
            printf("Item disponível! Processando pedido...\n");
            return item; 
            
            // Retorna o índice do item disponível
        } else {
            printf("Estoque esgotado. Verificando próximo item.\n");
        }
        item++;
    }
    
    // Retorna -1 se nenhum item estiver disponível
    return -1;
}

int main() {
    srand(time(0)); 
    
    // Inicializa o gerador de números aleatórios
    int num_pedidos = 10; 
    
    // Número de pedidos
    int pedidos[num_pedidos];
    int menu[5] = {5, 10, 15, 20, 25};
    // Tempos de preparo do menu
    int estoque[5] = {2, 0, 5, 1, 3}; 
    // Estoque dos itens do menu

    // 1. Simulando o atendimento de pedidos em uma fila (laço while)
    
    printf("Processando fila de pedidos:\n");
    int i = 0;
    while (i < num_pedidos) {
        pedidos[i] = menu[rand() % 5]; 
        
        // Atribui tempos de preparo aleatórios do menu
        printf("Pedido %d: tempo de preparo = %d minutos\n", i + 1, pedidos[i]);
        i++;
    }

    // 2. Verificando o menu (laço for)
    
    printf("\nVerificando o menu:\n");
    for (int j = 0; j < 5; j++) {
        printf("Item %d: tempo de preparo = %d minutos\n", j + 1, menu[j]);
    }

    // 3. Verificando estoque iterativamente usando função com laço while
    
    printf("\nVerificando estoque para o próximo pedido:\n");
    int item_disponivel = verificar_estoque(estoque, 5);
    if (item_disponivel == -1) {
        printf("Nenhum item disponível no estoque.\n");
    }

    // 4. Calculando o tempo total de preparo usando a função recursiva
    
    int total_tempo = calcular_tempo_total(pedidos, num_pedidos);
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

