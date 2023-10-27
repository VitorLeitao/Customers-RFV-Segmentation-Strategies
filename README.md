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
- Vamos agrupar os clientes e criar um novo DataFrame usando a data de sua última compra como referência. Em seguida, modificaremos uma coluna para refletir a diferença(em meses) entre a data de sua última compra e a última compra registrada no sistema. Isso nos permitirá determinar exatamente há quanto tempo o cliente não realiza uma compra.
- ![image](https://github.com/VitorLeitao/Customers-RFV-Segmentation-Strategies/assets/101846159/16b62af6-8c09-4af4-98e4-83ec2a3e5083)
- Apesar de a maioria dos valores estar abaixo de 10, identificamos outliers significativos, alguns chegando até 38. Isso indica que muitos clientes estão sem fazer compras há bastante tempo, próximos de dar Churn, considerando essa prolongada inatividade.
- ![image](https://github.com/VitorLeitao/Customers-RFV-Segmentation-Strategies/assets/101846159/b0bc7a32-a450-4ea4-bd96-4b5df5119d83)
- ![image](https://github.com/VitorLeitao/Customers-RFV-Segmentation-Strategies/assets/101846159/e24dccc7-9fe9-4f2b-8784-68d8fc9f78c6)
### 🔄**F**requência / 💰**V**alor
- Nesta fase, estaremos criando um novo conjunto de dados, também agrupado por cliente, mas desta vez realizaremos a contagem de suas transações de compra, juntamente com o cálculo da média de seus gastos em cada compra. Dessa forma, teremos uma visão detalhada sobre a frequência de suas compras e o valor médio gasto em cada transação.
- ![image](https://github.com/VitorLeitao/Customers-RFV-Segmentation-Strategies/assets/101846159/5bc25566-0a78-42ee-8630-9aea50fe8a6a)
- A frequência de compras exibe uma distribuição bastante regular, com apenas alguns outliers que elevam a média. Enquanto isso, o Valor Monetário apresenta numerosos outliers significativos, os quais explicam a disparidade entre a média e a mediana nos dados.
- ![image](https://github.com/VitorLeitao/Customers-RFV-Segmentation-Strategies/assets/101846159/b6d6803f-39dc-4c4a-b56f-1e1161046465)
- ![image](https://github.com/VitorLeitao/Customers-RFV-Segmentation-Strategies/assets/101846159/1c74d856-eb76-4b4d-8568-806ef2ac6d23)
### 🛠️Criando o DataFrame **RFV** final
- Nesta etapa, vamos simplesmente unir o conjunto de dados criado para analisar a recência com o conjunto de dados de frequência/valor, utilizando um inner join com base no identificador do cliente. Dessa forma, teremos todas as três informações de RFV consolidadas em um único conjunto de dados
- ![image](https://github.com/VitorLeitao/Customers-RFV-Segmentation-Strategies/assets/101846159/54ac5922-522e-4525-baa2-0b9c43b31ce1)
### 🔬Analisando o novo DataSet
- Inicialmente, não identificamos nenhuma correlação forte entre as características. A única correlação mínima encontrada foi entre Recência e Frequência, embora ainda seja bastante baixa. Apesar da sua baixa magnitude, esse dado revela que uma pequena parte dos clientes mantém uma relação inversamente proporcional entre frequência e recência. Ou seja, alguns clientes seguem a tendência de que, quanto mais frequentes são, mais recentes foram suas compras.A parte que deveria gerar preocupação, apesar de ser uma pequena parcela, são aqueles que estão no canto inferior direito do gráfico, que possuem baixa frequência e alta recência, ou seja, clientes que não compram frequentemente e não fazem compras há bastante tempo, são esses que tem a maior probabilidade de darem Churn:
- ![image](https://github.com/VitorLeitao/Customers-RFV-Segmentation-Strategies/assets/101846159/9ad2ebf9-e9b0-44ef-9ff6-b0af941d60af)

## 🤖Segmentação com KMeans
### 📉Visualização inicial da distribuição dos dados
- ![image](https://github.com/VitorLeitao/Customers-RFV-Segmentation-Strategies/assets/101846159/0f7450a3-8929-4da1-b32b-c943f377474c)
### 📏Método do cotovelo
- ![image](https://github.com/VitorLeitao/Customers-RFV-Segmentation-Strategies/assets/101846159/3d21dfbc-12fc-4f06-a061-2f96acae2940)
- Na teoria, a quantidade de cluster mais apropriada para esse conjunto de dados seria, possivelmente,  3, porém para o mundo dos negócios talvez seja uma segmentação com poucos grupos, o ideal seria testar algum valor entre 3~6
### 🧪Modelagem e aplicação 
- Após o escalonamento dos dados e a aplicação do GridSearchCV
 para determinar os melhores parâmetros, aplicamos o KMeans no conjunto de dados e tivemos esses resultados: 
- ![image](https://github.com/VitorLeitao/Customers-RFV-Segmentation-Strategies/assets/101846159/36a7862d-7693-429e-9cdc-35bb593a1451)
- Visualização das informações de cada cluster:
- ![image](https://github.com/VitorLeitao/Customers-RFV-Segmentation-Strategies/assets/101846159/e3c2c182-f701-4a22-b20d-012c206be1de)
- Os insights derivados deste modelo revelam quatro grupos distintos: Clientes VIP, Possíveis Churn, Clientes Engajados e Clientes Regulares. Sendo os VIP aqueles com maior valor monetário em suas compras; possíveis churns aqueles que estão há muito tempo sem comprar; engajados aqueles com uma alta frequência; e regulares os que não tem nenhum atributo outlier, estando próximo da média em todos, ou seja, nem é um cliente extraordinário nem um possível churn, estando no meio termo. Para simplificar a interpretação, mapeamos os números dos clusters para suas categorias correspondentes, proporcionando uma compreensão mais intuitiva da segmentação dos clientes
- ![image](https://github.com/VitorLeitao/Customers-RFV-Segmentation-Strategies/assets/101846159/ef2cbcde-96c5-459b-9012-f442c0639b1b)









   


