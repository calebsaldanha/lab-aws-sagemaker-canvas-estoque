# Previsão inteligente de estoque 

## Introdução

Neste projeto, desenvolvi um modelo de aprendizado de máquina para previsão de estoque usando Amazon Sagemaker Canvas. O objetivo é criar um sistema inteligente que utilize dados históricos para prever os volumes de vendas necessários para auxiliar no gerenciamento de estoque e na tomada de decisões. A seguir explicarei passo a passo o processo, detalhando o processo, as premissas envolvidas, as decisões envolvidas e a análise dos resultados esperados.

## Passo a passo ###

 O primeiro passo neste projeto é selecionar um conjunto de dados apropriado. Fui até a pasta “Datasets” do repositório e lá vi diversas opções de processamento de dados. Depois de revisar os dados disponíveis, selecionei um conjunto de dados que continha informações do produto, incluindo preço, critérios de suporte e quantidades do produto. SelecioneI o dataset/dataset-1000-com-preco-promocional-e-renovacao-estoque.csv. Após selecionar o conjunto de dados, carreguei-o no SageMaker Canvas, uma ferramenta para criação, treinamento e implantação de plataforma de modelo de aprendizado de máquina.
Importei o conjunto de dados selecionado para o SageMaker Canvas. Configurei as variáveis ​​de entrada e saída e a coluna que desejo reportar é "STOCK_QUANTITY". O modelo foi projetado para realizar previsões sistemáticas, o que inclui a previsão de padrões futuros com base em dados passados. Comecei a treinar como modelo. Nesse caso, quando eu estava trabalhando na amostra, o tempo foi curto. O modelo usa dados passados ​​para prever os níveis futuros de estoque.

Avaliei os parâmetros de desempenho do modelo. Isto é fundamental para compreender a eficácia do modelo e se ele está fazendo previsões precisas. As principais coisas que verifico são: 

** Avg. wQL**: 0,457 
**MAPE** (erro percentual médio absoluto): 0,331
**WAPE** (erro percentual absoluto): 0,715
**RMSE** (erro quadrático médio): 24,160
* *MASE **(Erro Médio Absoluto): 0,000
* 
Esses parâmetros mostram a precisão da previsão e ajudam a identificar áreas de melhoria. Durante a análise, constatei que a coluna “FLAG_PROMOOCAO” teve um impacto negativo na previsão, apresentando uma precisão de -100%. Isso me faz pensar em fazer alterações no modelo, como remover ou modificar essa variável.
Extraí os resultados e analisei as previsões feitas. Este processo envolve observar o desempenho das quantidades esperadas em relação às expectativas e identificar quaisquer padrões ou insights que possam ser úteis no gerenciamento de estoque.

###Análise Preditiva####

A análise de dados fornece previsões de estoque de vários produtos para o dia seguinte (09/02/2024). Cada produto possui três percentuais (p10, p50, p90) e uma previsão.
####Porcentagem de descrição - **p10**: Este valor representa a previsão de segurança, indicando a quantidade de produtos que podem passar em 90% dos casos. É importante entender o contexto dessa pequena expectativa.
**p50***: Este valor representa uma previsão de estoque, indicando um cenário mais ideal.
**p90***: Este valor representa uma previsão brilhante indicando que as dimensões do produto podem ser excedidas em apenas 10% dos casos.

#### Insight Data - Por exemplo, a previsão média ("média") para produto com "Product_ID" 1005 é de 40,90 minutos. Na melhor das hipóteses (`p10`) o produto pode ser reduzido em até 4 unidades e na melhor das hipóteses (`p90`) o produto pode chegar a 79 unidades - a diferença entre as porcentagens mostra a Incerteza do 'mundo real'. política. Produtos com diferenças maiores entre “p10” e “p90” indicam maiores mudanças na demanda esperada, enquanto produtos com diferenças percentuais menores indicam previsões estáveis.
#### PRODUTOS ESPECIAIS - **PRODUTO 1003**: A previsão é de 6,46 minutos, possivelmente subindo para -10,08 no pior cenário (`p10`) e acima (indicando seu possível enfraquecimento). 29.19 Melhor da Mostra (`p90`). - **Produto 1004***: Mostra previsões para 10,50 unidades, variando de -11,57 (`p10`) a 36,93 (`p90`). - **1000 Ações***: A previsão é de 2,20 unidades, com intervalo de -16,15 (`p10`) a 24,61 (`p90`).
