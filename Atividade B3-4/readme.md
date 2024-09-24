
# Análise de Desempenho de Algoritmos - Proposta de Solução Computacional

**Equipe:**

- Rafael Willian Galindo Neto
- Murilo Grillo Bastos
- Giovanni Montteiro
- Vitor Tamais Fischer

**Curso:** ADS - Análise e Desenvolvimento de Sistemas  
**Disciplina:** Estrutura de Dados  
**Data:** [## - ## - ####]  

## Descrição do Negócio

O projeto envolve a criação de uma solução computacional para otimizar o sistema de gestão de atendimento de um restaurante, que enfrenta desafios na organização e análise de pedidos durante o atendimento. A necessidade é desenvolver um programa que simule a fila de atendimento, verificação do menu e controle de estoque, além de calcular o tempo total de preparo dos pedidos.

O objetivo principal é melhorar a eficiência do atendimento, ajustando os tempos de espera de acordo com a complexidade dos pedidos e fornecer uma base para análise de desempenho dos algoritmos utilizados.

### Requisitos do Sistema:

- **Gestão de Pedidos:** Processamento e organização dos pedidos, com controle dos tempos de preparo e gestão de fila.
- **Verificação de Menu:** Análise do tempo de preparo dos itens do menu para melhor gerenciamento dos recursos de cozinha.
- **Controle de Estoque:** Garantia de que os itens necessários estão disponíveis para o preparo dos pedidos.
- **Cálculo do Tempo de Atendimento:** Ajustar o tempo total de atendimento conforme a complexidade dos pedidos utilizando iterações.

## Macro Solução

Para atender a essas necessidades, o sistema será implementado utilizando três laços de repetição, garantindo que os processos de atendimento sejam realizados de forma eficiente. A seguir, detalhamos os principais componentes da solução:

### Estrutura da Solução:

1. **Fila de Atendimento (Laço While):** O sistema simula o atendimento de pedidos em uma fila usando um laço `while`, processando cada pedido sequencialmente até que todos sejam atendidos.

2. **Consulta de Menu (Laço For):** Utiliza-se um laço `for` para iterar sobre os itens do menu, permitindo visualizar os tempos de preparo e ajustar o atendimento conforme necessário.

3. **Verificação de Estoque (Laço While Iterativo):** A verificação do estoque é realizada através de um laço iterativo que garante que apenas os itens disponíveis sejam utilizados, prevenindo atrasos no atendimento devido à falta de produtos.

4. **Cálculo do Tempo Total de Atendimento (Função Iterativa):** Uma função iterativa calcula o tempo total de atendimento, ajustando o tempo de espera de acordo com a complexidade de cada pedido. A função percorre todos os pedidos, somando os tempos de preparo e ajustando conforme necessário para refletir a complexidade.

### Código em Python

```python
import random

def calcular_tempo_total(pedidos):
    total = 0
    for tempo in pedidos:
        total += tempo
    return total

def verificar_estoque(estoque):
    for item in range(len(estoque)):
        print(f"Verificando estoque do item {item + 1}... ", end="")
        if estoque[item] > 0:
            print("Item disponível! Processando pedido...\n")
            return item  # Retorna o índice do item disponível
        else:
            print("Estoque esgotado. Verificando próximo item.")
    return -1  # Retorna -1 se nenhum item estiver disponível

def main():
    random.seed()  # Inicializa o gerador de números aleatórios

    num_pedidos = int(input("Digite o número de pedidos: "))
    pedidos = []
    menu = []
    estoque = []

    # Entrada de dados do menu
    print("\nDigite os tempos de preparo dos 5 itens do menu (em minutos):")
    for i in range(5):
        tempo = int(input(f"Tempo de preparo do item {i + 1}: "))
        menu.append(tempo)

    # Entrada de dados do estoque
    print("\nDigite as quantidades em estoque dos 5 itens do menu:")
    for i in range(5):
        quantidade = int(input(f"Quantidade em estoque do item {i + 1}: "))
        estoque.append(quantidade)

    # Processando pedidos
    print("\nProcessando fila de pedidos:")
    for i in range(num_pedidos):
        pedido = menu[random.randint(0, 4)]  # Atribui tempos de preparo aleatórios do menu
        pedidos.append(pedido)
        print(f"Pedido {i + 1}: tempo de preparo = {pedido} minutos")

    # Verificando o menu
    print("\nVerificando o menu:")
    for j in range(5):
        print(f"Item {j + 1}: tempo de preparo = {menu[j]} minutos")

    # Verificando estoque
    print("\nVerificando estoque para o próximo pedido:")
    item_disponivel = verificar_estoque(estoque)
    if item_disponivel == -1:
        print("Nenhum item disponível no estoque.\n")

    # Calculando o tempo total de preparo
    total_tempo = calcular_tempo_total(pedidos)
    print(f"\nTempo total de preparo dos pedidos: {total_tempo} minutos")

if __name__ == "__main__":
    main()





### Explicação do Código

O código é um sistema simples para gerenciar pedidos em um restaurante, utilizando Python. Ele inclui funções para calcular o tempo total de preparo dos pedidos e verificar a disponibilidade dos itens no estoque. A seguir, explicamos as principais funções do código:

- **Função `calcular_tempo_total(pedidos):`**
  - **Descrição:** Esta função recebe uma lista de tempos de preparo dos pedidos e calcula o tempo total somando todos os elementos.
  - **Funcionamento:** Utiliza um laço `for` para iterar sobre cada elemento da lista `pedidos`, acumulando o tempo em uma variável `total`, que é retornada ao final da função.

- **Função `verificar_estoque(estoque):`**
  - **Descrição:** Esta função percorre a lista de estoques para verificar a disponibilidade dos itens.
  - **Funcionamento:** Utiliza um laço `for` que itera através dos índices dos itens no estoque. Para cada item, imprime o status de disponibilidade e retorna o índice do primeiro item disponível ou -1 se nenhum item estiver disponível.

- **Função `main():`**
  - **Descrição:** Esta é a função principal que gerencia a execução do programa.
  - **Funcionamento:** A função solicita a entrada do usuário para o número de pedidos, os tempos de preparo do menu e as quantidades em estoque. Em seguida, simula o processamento dos pedidos, verifica o menu e o estoque, e calcula o tempo total de preparo utilizando as funções anteriormente descritas.

### Resumo do Fluxo do Programa

1. O usuário é solicitado a inserir o número de pedidos e os tempos de preparo dos itens do menu.
2. O estoque dos itens também é solicitado.
3. O sistema processa os pedidos gerando tempos de preparo aleatórios a partir do menu.
4. O sistema verifica a disponibilidade dos itens no estoque.
5. Finalmente, o tempo total de preparo dos pedidos é calculado e exibido.

### Interatividade e Desempenho

O sistema é projetado para ser interativo e permite ao usuário inserir dados de forma simples. A implementação de laços de repetição (loops) assegura que o sistema possa gerenciar um número variável de pedidos, tornando-o escalável. As funções são estruturadas para promover clareza e eficiência, o que facilita futuras otimizações e melhorias.
