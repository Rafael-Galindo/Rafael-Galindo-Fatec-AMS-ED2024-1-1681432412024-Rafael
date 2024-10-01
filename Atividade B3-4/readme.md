# Sistema de Gerenciamento de Pedidos

## Componentes da Equipe
- Rafael Willian Galindo Neto
- [Murilo Grillo Bastos]
- [Vitor Tamais Fischer]
- [Giovanni Montteiro]

## Descrição de Negócio
O Sistema de Gerenciamento de Pedidos foi desenvolvido para otimizar o atendimento ao cliente em um ambiente de restaurante. A proposta é permitir que os operadores do restaurante gerenciem pedidos de forma eficiente, garantindo a verificação do estoque e o cálculo do tempo de preparo dos itens do menu. O sistema é interativo e permite a entrada de dados em tempo real, proporcionando uma experiência fluida tanto para os operadores quanto para os clientes.


## Problema Proposto/Solução Proposta

Este projeto foi desenvolvido para atender a um problema comum enfrentado por restaurantes: **a gestão eficiente dos pedidos e do estoque**. O sistema permite que os restaurantes processem pedidos de forma organizada e monitorem a disponibilidade dos itens no estoque, evitando atrasos no atendimento e a insatisfação dos clientes.

As principais questões que o sistema busca resolver incluem:

1. **Eficiência no Atendimento:** Automatizar o processo de recebimento e processamento de pedidos, reduzindo o tempo de espera para os clientes.
2. **Gestão do Estoque:** Permitir que os gerentes de restaurante verifiquem rapidamente a disponibilidade dos itens, evitando vendas de produtos esgotados.
3. **Planejamento de Preparo:** Proporcionar uma visão clara do tempo de preparo total dos pedidos, facilitando a programação da equipe de cozinha.

Dessa forma, o sistema contribui para um atendimento mais ágil e eficiente, aumentando a satisfação do cliente e melhorando a operação do restaurante.



## Requisitos do Sistema
### Funcionais
1. **Entrada de Dados:**
   - O sistema deve permitir que o usuário insira o número de pedidos, os tempos de preparo dos itens do menu e as quantidades disponíveis em estoque.
2. **Processamento de Pedidos:**
   - O sistema deve gerar pedidos aleatórios a partir do menu e calcular o tempo total de preparo.
3. **Verificação de Estoque:**
   - O sistema deve verificar se os itens necessários estão disponíveis em estoque antes de processar os pedidos.
4. **Atualização de Estoque:**
   - O sistema deve atualizar a quantidade em estoque após cada pedido ser processado.
5. **Continuação de Pedidos:**
   - O sistema deve permitir que o usuário continue processando pedidos até que o estoque se esgote ou que o usuário decida parar.

### Não Funcionais
1. **Usabilidade:**
   - O sistema deve ser intuitivo e fácil de usar para o operador.
2. **Desempenho:**
   - O sistema deve processar pedidos rapidamente, mesmo com múltiplos pedidos em sequência.
3. **Confiabilidade:**
   - O sistema deve funcionar de forma consistente e correta, sem falhas que comprometam o atendimento.

## Resumo do Código
O código implementa um sistema de gerenciamento de pedidos utilizando Python. Ele inclui as seguintes funcionalidades:

1. **Entrada de Dados:** O usuário é solicitado a informar o número de pedidos, os tempos de preparo dos itens do menu e as quantidades disponíveis em estoque.
2. **Processamento de Pedidos:** O sistema gera pedidos aleatórios, calcula o tempo de preparo total e verifica a disponibilidade dos itens no estoque.
3. **Verificação de Estoque:** O sistema checa se os itens necessários estão disponíveis antes de processar cada pedido.
4. **Atualização de Estoque:** Após o processamento de um pedido, o estoque é atualizado para refletir a quantidade disponível.
5. **Repetição:** O sistema permite ao usuário continuar processando pedidos até que o estoque esgote ou o usuário decida parar.

## Resumo do Fluxo do Programa
O fluxo do programa é o seguinte:

1. **Início:** O programa inicia e solicita ao usuário o número de pedidos, tempos de preparo dos itens do menu e quantidades em estoque.
2. **Entrada de Dados:** O usuário insere os tempos de preparo dos itens e as quantidades em estoque.
3. **Processamento de Pedidos:** O programa entra em um laço onde processa os pedidos, gerando pedidos aleatórios do menu e verificando a disponibilidade dos itens no estoque.
4. **Verificação de Estoque:** Para cada pedido, o programa verifica se o item está disponível no estoque. Se disponível, o pedido é processado; se não, o programa informa que não há itens disponíveis.
5. **Atualização do Estoque:** O estoque é atualizado após cada pedido processado.
6. **Continuação:** O programa pergunta ao usuário se deseja continuar processando mais pedidos. Se sim, o laço recomeça; se não, o programa termina.
7. **Cálculo do Tempo Total:** Após o término dos pedidos, o programa calcula e exibe o tempo total de preparo dos pedidos.
8. **Fim:** O programa finaliza.


## Macro Solução
A solução proposta consiste em um sistema que possui as seguintes características:

- **Entrada de Dados:** O sistema solicita ao usuário informações sobre o número de pedidos, tempos de preparo e quantidades em estoque dos itens do menu.
- **Laços de Repetição:**
  - **`for` Loop:** Utilizado para calcular o tempo total de preparo dos pedidos e para verificar a disponibilidade de itens no estoque.
  - **`while` Loop:** Permite que o sistema continue processando pedidos até que o estoque esgote ou o usuário decida parar.

## Ferramentas e Linguagens Utilizadas
- **Linguagem de Programação:** Python
  - A escolha do Python se deve à sua simplicidade e expressividade, que facilita o desenvolvimento de soluções rápidas e eficientes.
- **Ferramentas:**
  - Python 3.x: Para o desenvolvimento da aplicação.
  - GitHub: Utilizado para controle de versão e colaboração entre os membros da equipe.


# A) Evolução da Análise

## Introdução à Análise Assintótica

A análise assintótica é um método utilizado para descrever o comportamento de algoritmos em termos de tempo de execução e uso de memória à medida que a entrada cresce. Este conceito é fundamental no desenvolvimento de software eficiente.

## Objetivos do Projeto

O sistema de gestão de pedidos foi projetado para otimizar o atendimento ao cliente em restaurantes, processando pedidos e verificando a disponibilidade de itens no estoque.

## Estrutura do Código

O sistema utiliza iteração para processar pedidos e verificar o estoque, com laços de repetição e uma função recursiva, o que permite que o programa opere de forma eficiente e escalável.

## Cenários de Execução

- **Melhor Caso:** Quando há sempre itens disponíveis no estoque e o número de pedidos é pequeno, o tempo de execução é reduzido, pois o sistema rapidamente processa cada pedido.
- **Pior Caso:** Ocorre quando o estoque está quase esgotado, exigindo várias verificações de estoque, ou quando o número de pedidos é elevado, aumentando o tempo total de processamento.

## Crescimento das Funções

À medida que o número de pedidos e a complexidade do menu aumentam, a análise deve considerar como a quantidade de pedidos e o tamanho do estoque afetam o desempenho do sistema.

# B) Função Assintótica [Simplificação]

Para simplificar a função assintótica do nosso projeto, analisaremos as partes mais críticas do código:

## Funções Principais

- **`calcular_tempo_total(pedidos):`** Esta função percorre todos os pedidos e calcula o tempo total.
  - **Complexidade:** \(O(n)\), onde \(n\) é o número de pedidos.

- **`verificar_estoque(estoque):`** Esta função percorre o estoque para verificar a disponibilidade de itens.
  - **Complexidade:** \(O(m)\), onde \(m\) é o número de itens no estoque.

- **`main():`** Esta função contém um laço while que continua processando pedidos até que não haja mais itens disponíveis ou o usuário decida parar.
  - A complexidade total do laço depende do número de iterações que ele faz, que pode ser um número \(k\) de pedidos em cada iteração. Portanto, o tempo total do laço pode ser expresso como:
  \[
  O(k \cdot n) \text{ (para processar os pedidos)} + O(k \cdot m) \text{ (para verificar o estoque)} = O(k \cdot (n + m))
  \]

## Função Assintótica Final

A complexidade total do sistema pode ser expressa como:
\[
O(n + m + k \cdot (n + m))
\]
Esta função indica que o tempo de execução do sistema aumenta linearmente com o número de pedidos e itens no estoque, e a interação entre os pedidos e as verificações de estoque.

# Conclusão

A análise assintótica do nosso projeto de sistema de gestão de pedidos revela que a eficiência do código é crucial para a operação em ambientes com alta demanda. O uso de funções lineares e iterações permite que o sistema mantenha um desempenho adequado, mesmo com o crescimento da quantidade de pedidos e do estoque. Essa análise ajuda a identificar pontos de melhoria e otimização para o futuro.



### Código em Python

```python
import random

def calcular_tempo_total(pedidos):
    return sum(pedidos)

def verificar_estoque(estoque):
    for i, item in enumerate(estoque):
        if item > 0:
            return i  # Retorna o índice do primeiro item disponível
    return -1  # Retorna -1 se nenhum item estiver disponível

def main():
    random.seed()  # Inicializa o gerador de números aleatórios

    num_pedidos = int(input("Digite o número inicial de pedidos: "))
    menu = [int(input(f"Digite o tempo de preparo do item {i + 1} (em minutos): ")) for i in range(5)]
    estoque = [int(input(f"Digite a quantidade em estoque do item {i + 1}: ")) for i in range(5)]

    pedidos = []

    while True:
        print("\nProcessando pedidos:")
        for _ in range(num_pedidos):
            item_index = random.randint(0, 4)  # Seleciona aleatoriamente um item do menu
            if estoque[item_index] > 0:  # Verifica se o item está disponível
                pedidos.append(menu[item_index])
                estoque[item_index] -= 1
                print(f"Pedido processado: tempo de preparo = {menu[item_index]} minutos")
            else:
                print(f"Item {item_index + 1} esgotado!")

        if verificar_estoque(estoque) == -1:
            print("Nenhum item disponível no estoque.")
            break

        continuar = input("Deseja continuar processando mais pedidos? (s/n): ")
        if continuar.lower() != 's':
            break
        num_pedidos = int(input("Digite o número de novos pedidos: "))

    total_tempo = calcular_tempo_total(pedidos)
    print(f"\nTempo total de preparo dos pedidos: {total_tempo} minutos")

if __name__ == "__main__":
    main()
´´´


