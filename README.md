# Customers-RFV-Segmentation-Strategies
## 🔍 Sobre o projeto
### Analise de RFV: Superstore Sales Dataset
Análise de RFV(Recência, Frequência e Valor): Este notebook realiza uma análise aprofundada da base de dados do kaggle(https://www.kaggle.com/datasets/rohitsahoo/sales-forecasting) usando a técnica RFV (Recência, Frequência, Valor) e algoritmos de cluster. Exploramos padrões de compra dos clientes e identificamos grupos com comportamentos semelhantes. Os insights obtidos ajudarão a personalizar estratégias de marketing, melhorando a experiência do cliente e impulsionando o crescimento do negócio.
### Sobre o Dataset
Esse dataset possui informações extremamente valiosas para a anlise de RFV, como o identificador de cliente, data da compra e preço, entre outras features interessantes como a localização dos usuários e as categorias dos produtos comprados
- ![image](https://github.com/VitorLeitao/Customers-RFV-Segmentation-Strategies/assets/101846159/a4f52245-3731-4c31-bb0b-1f6ff0a96b1b)
### 🎯 Objetivos do Projeto
1. **Compreensão Profunda dos Padrões de Compra dos Clientes**: Identificar comportamentos de compra recorrentes, sazonais ou específicos a determinados grupos de clientes.
2. **Segmentação Eficiente dos Clientes**: Aplicar algoritmos de cluster para segmentar os clientes com base em seu comportamento de compra, criando grupos distintos e identificando perfis de clientes.
3. **Impulsionar o Crescimento do Negócio**: Utilizar os insights derivados da análise de RFV para impulsionar o crescimento do negócio, aumentando as vendas, a fidelidade do cliente e a participação de mercado.

## 🗺️ Exploração inicial da base de dados
De início não foi preciso muito trabalho em relação à pré processamento dos dados, a única inconsistência que estava presente na base era alguns missings na coluna de caixa postal, mas como esse notebook se trata de uma análise de RFV, é necessário apenas as features relacionados a identificação dos clientes, data e valor da compra, então apenas excluímos essa feature inconsistente.
### 📊insights iniciais
1. - A maioria esmagadora das vendas se situa na faixa de U$20 a U$200. No entanto, é importante notar a presença significativa de outliers extremamente fortes, cujos valores alcançam impressionantes U$22.638, indicando uma ampla variedade nos montantes das vendas.
- ![image](https://github.com/VitorLeitao/Customers-RFV-Segmentation-Strategies/assets/101846159/a043bfaa-2ea2-4e2e-8125-99affdfadb70)
2. - A maioria esmagadora das vendas se situa na faixa de U$20 a U$200. No entanto, é importante notar a presença significativa de outliers extremamente fortes, cujos valores alcançam impressionantes U$22.638, indicando uma ampla variedade nos montantes das vendas.
- ![image](https://github.com/VitorLeitao/Customers-RFV-Segmentation-Strategies/assets/101846159/a043bfaa-2ea2-4e2e-8125-99affdfadb70)


