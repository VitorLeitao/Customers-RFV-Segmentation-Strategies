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
1. A maioria esmagadora das vendas se situa na faixa de U$20 a U$200. No entanto, é importante notar a presença significativa de outliers extremamente fortes, cujos valores alcançam impressionantes U$22.638, indicando uma ampla variedade nos montantes das vendas.
![image](https://github.com/VitorLeitao/Customers-RFV-Segmentation-Strategies/assets/101846159/a043bfaa-2ea2-4e2e-8125-99affdfadb70)
2. Analisando a segmentação geográfica, é possível identificar as regiões de maior valor total de venda na empresa, que opera exclusivamente nos Estados Unidos. As principais áreas de vendas estão localizadas na costa leste e oeste do país, com foco particular nos estados de Los Angeles e New York. 
![image](https://github.com/VitorLeitao/Customers-RFV-Segmentation-Strategies/assets/101846159/b501750b-7dae-43cb-a735-7db81269465f)
3. A análise das preferências de categoria em diversas regiões dos Estados Unidos revelou um padrão consistente: a preferência dominante por artigos de escritório ('office supplies') é evidente em todas as regiões, enquanto as vendas de móveis ('furniture') e tecnologia ('technology') estão praticamente empatadas, apesar da ligeira vantagem de 'office supplies' na maioria dos casos. Talvez seja eficiente investimento em propaganda ou promoções para essas categorias menos procuradas.
![image](https://github.com/VitorLeitao/Customers-RFV-Segmentation-Strategies/assets/101846159/07daa53f-eedc-4def-854f-dff71702778d)
4.  As categorias com os maiores valores de mercado são furniture e tecnologia, mas em média Furniture tem um valor médio um pouco maior, apesar disso, os produtos de tecnologia tem uma escalabilidade maior em relação ao preço, tendo os outliers mais altos.
- Furniture: ![image](https://github.com/VitorLeitao/Customers-RFV-Segmentation-Strategies/assets/101846159/d5e003df-f3ee-4c28-97e9-d4edb13f7a71)
- Technology: ![image](https://github.com/VitorLeitao/Customers-RFV-Segmentation-Strategies/assets/101846159/7bd1e8c7-3fb2-4a39-8d34-1309444fcc20)
  
## 🧩Montagem do dataset RFV
Agora, vamos criar um novo conjunto de dados que incluirá informações sobre cada cliente que fez compras na empresa. Para cada cliente, teremos dados sobre a 'recência' (tempo desde sua última compra), 'frequência' (número de compras feitas durante o período abrangido pelos dados) e 'valor' (média de gastos em suas compras na empresa).
### 🕒**R**ecência



   


