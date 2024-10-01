# Sistema de Gerenciamento de Pedidos

## Componentes da Equipe
- Rafael Willian Galindo Neto
- [Murilo Grillo Bastos]
- [Vitor Tamais Fischer]
- [Giovanni Montteiro]

## Descrição de Negócio
O Sistema de Gerenciamento de Pedidos foi desenvolvido para otimizar o atendimento ao cliente em um ambiente de restaurante. A proposta é permitir que os operadores do restaurante gerenciem pedidos de forma eficiente, garantindo a verificação do estoque e o cálculo do tempo de preparo dos itens do menu. O sistema é interativo e permite a entrada de dados em tempo real, proporcionando uma experiência fluida tanto para os operadores quanto para os clientes.

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


