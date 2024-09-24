# Análise de Desempenho de Algoritmos

**Equipe:**

- Rafael Willian Galindo Neto
- Murilo Grillo Bastos
- Giovanni Montteiro
- Vitor Tamais Fischer

Data: [##-##-####]


## Descrição de Negócio

O problema que abordaremos consiste em desenvolver uma solução computacional para simular o funcionamento de um sistema de gestão de filas em um restaurante, onde diferentes processos são gerenciados com base no estado de atendimento. A eficiência do atendimento será otimizada utilizando laços de repetição e iteração, permitindo que o sistema escale adequadamente à medida que o número de pedidos cresce.


## Macro Solução

A solução envolve três laços de repetição para os seguintes processos:

1. **Fila de atendimento**: Um laço `while` que processa pedidos até que todos sejam atendidos.
2. **Consulta de menu**: Um laço `for` para iterar sobre os itens do menu, calculando o tempo de preparo de cada pedido.
3. **Verificação de estoque**: Um laço `do-while` que continua verificando os níveis de estoque até que seja possível preparar o próximo pedido.

Além disso, utilizar uma função de iteração que será usada para calcular o tempo total de atendimento, levando em conta a iteração para ajustar o tempo de espera de acordo com a complexidade dos pedidos


## Ferramentas e Linguagens

- **Linguagem de Programação:** C (escolhida por seu desempenho e controle detalhado de memória).
- **Ferramentas:** GCC (GNU Compiler Collection) para compilar o código, e Github para controle de versão e colaboração.


Código em Python:
import random
import time

# Função iterativa para calcular o tempo total de preparo dos pedidos
def calcular_tempo_total(pedidos):
    total = 0
    for tempo in pedidos:
        total += tempo
    return total

# Função para ajustar o tempo de atendimento com base na complexidade dos pedidos
def ajustar_tempo(pedidos):
    total_ajustado = 0
    for tempo in pedidos:
        # Complexidade ajustada: quanto maior o tempo, mais complexo
        # Adiciona um fator de ajuste ao tempo de espera baseado na complexidade
        if tempo > 20:
            fator_ajuste = 10  # Ajuste para pedidos mais complexos
        elif tempo > 10:
            fator_ajuste = 5   # Ajuste médio
        else:
            fator_ajuste = 2   # Ajuste para pedidos menos complexos

        total_ajustado += tempo + fator_ajuste
    return total_ajustado

# Função para verificar estoque de forma iterativa
def verificar_estoque(estoque):
    item = 0
    while item < len(estoque):
        print(f"Verificando estoque do item {item + 1}... ", end="")
        if estoque[item] > 0:
            print("Item disponível! Processando pedido...")
            return item  # Retorna o índice do item disponível
        else:
            print("Estoque esgotado. Verificando próximo item.")
        item += 1
    return -1

# Função principal
def main():
    random.seed(time.time())  # Inicializa o gerador de números aleatórios

    num_pedidos = int(input("Digite o número de pedidos: "))

    pedidos = [0] * num_pedidos
    menu = []
    estoque = []

    # Entrada de dados do menu
    print("\nDigite os tempos de preparo dos 5 itens do menu (em minutos):")
    for i in range(5):
        tempo_preparo = int(input(f"Tempo de preparo do item {i + 1}: "))
        menu.append(tempo_preparo)

    # Entrada de dados do estoque
    print("\nDigite as quantidades em estoque dos 5 itens do menu:")
    for i in range(5):
        quantidade_estoque = int(input(f"Quantidade em estoque do item {i + 1}: "))
        estoque.append(quantidade_estoque)

    # 1. Simulando o atendimento de pedidos em uma fila (laço while)
    print("\nProcessando fila de pedidos:")
    i = 0
    while i < num_pedidos:
        pedidos[i] = random.choice(menu)  # Atribui tempos de preparo aleatórios do menu
        print(f"Pedido {i + 1}: tempo de preparo = {pedidos[i]} minutos")
        i += 1

    # 2. Verificando o menu (laço for)
    print("\nVerificando o menu:")
    for j, tempo in enumerate(menu):
        print(f"Item {j + 1}: tempo de preparo = {tempo} minutos")

    # 3. Verificando estoque iterativamente usando função com laço while
    print("\nVerificando estoque para o próximo pedido:")
    item_disponivel = verificar_estoque(estoque)
    if item_disponivel == -1:
        print("Nenhum item disponível no estoque.")

    # 4. Calculando o tempo total de preparo usando a função iterativa
    total_tempo = calcular_tempo_total(pedidos)
    print(f"\nTempo total de preparo dos pedidos (sem ajustes): {total_tempo} minutos")

    # 5. Ajustando o tempo de atendimento com base na complexidade dos pedidos
    total_tempo_ajustado = ajustar_tempo(pedidos)
    print(f"Tempo total de preparo ajustado com complexidade: {total_tempo_ajustado} minutos")

if __name__ == "__main__":
    main()


