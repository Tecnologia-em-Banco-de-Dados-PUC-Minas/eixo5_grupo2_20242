# Etapa 5 - ANÁLISE DOS RESULTADOS

Nesta etapa do projeto, apresentaremos os resultados obtidos a partir dos treinamentos dos modelos realizados com um arquivo que representa 10% do total dos nossos dados da base de Atletas. 
A escolha desse percentual foi necessária devido a limitações relacionadas ao processamento e à memória disponíveis nas versões gratuitas do Google Colab e do SageMaker. 
Portanto, consideramos 10% como uma amostra aceitável para os testes realizados, garantindo a viabilidade dos experimentos apresentados a seguir.
  
## Análise dos Resultado - SageMaker 

### Construído  o modelo

Para a criação do modelo no SageMaker, utilizamos a opção de construção rápida onde o tempo estimado para o processo varia entre 2 e 15 minutos. 
O dataset que utilizamos contém 12 colunas e 271.116 linhas e o processamento executado nessa etapa verifica o impacto das colunas que serão utilizadas, o que significa que o algoritmo irá determinar quais variáveis possuem maior relevância para as predições.

![image](https://github.com/user-attachments/assets/ca399740-3a39-4df2-a523-d791f626ff6d)

### Análisando os Resultados - Tela Overview

Após a conclusão do processamento, na aba de Overview o modelo apresentou uma acurácia de 88,724%, indicando que realizou predições corretas na grande maioria dos casos.O F1-Score foi de 0,631, demonstrando um bom desempenho no equilíbrio entre precisão e sensibilidade. 
A taxa de erro do modelo nesta versão foi de 11,276%. Esse valor é obtido calculando a diferença entre 100% e a acurácia do modelo.

Na sessão onde é apresentado as colunas impactadas, a coluna com a maior relevância no modelo foi a “NOC”, com um valor de 33,685%, seguida da “Event” (16,663%) e a “Team” (15,625%). Por outro lado, as colunas relacionadas às 
características físicas dos atletas apresentaram impacto menor do que o esperado. Esse resultado foi interessante, pois inicialmente esperava-se que variáveis como peso, 
altura e idade tivessem maior relevância nos resultados do treinamento.

![image](https://github.com/user-attachments/assets/bdd35715-33e8-44f2-9b92-d0fc7478df7b)

### Análisando os Resultados - Tela Scoring 

Ao analisar os resultados na aba Scoring, é possível observar no gráfico "Predicted vs. Actual" o total de registros utilizados no modelo, que corresponde a 9.995 registros. 
Esses registros foram classificados nas categorias 0 (não ganharam medalha) e 1 (ganharam medalha).
O modelo demonstrou um excelente desempenho na previsão da classe "0", acertando em 94,006% dos casos. 
Por outro lado, para a classe "1", o modelo apresentou maior dificuldade em identificar corretamente os atletas que ganharam medalhas, resultando em uma eficiência geral mais baixa para essa classe. 
Esse desempenho desigual sugere que o modelo é mais confiável para prever atletas que não ganhariam medalhas do que para aqueles que ganhariam. 
Esse comportamento era esperando pois em nossa base a mais atletas que não ganharam medalha do que atletas que ganharam medalhas.

![image](https://github.com/user-attachments/assets/756f9141-ef70-441e-a6ae-9f7e13c2afb9)

### Análisando os Resultados - Tela Advanced metrics

Analisando os resultados na aba Advanced Metrics, além das métricas previamente mencionadas, o SageMaker também gerou uma Matriz de Confusão com os dados classificados, como mostrado na imagem abaixo. 
A partir dessa análise, observa-se que o modelo tem melhor desempenho na previsão da classe negativa, com uma taxa de acerto de 79,1%. 
Conforme mencionado na seção anterior, o modelo demonstra maior eficiência na identificação de atletas que não ganhariam uma medalha, em comparação com sua capacidade de identificar aqueles que ganhariam.

Nesta versão, obtivemos os seguintes resultados:

  •	**Precisão**: 60,774% – indicando que apenas cerca de 60,8% das predições positivas feitas pelo modelo estavam corretas.
  
  •	**Recall**: 65,668% – mostrando que o modelo conseguiu identificar corretamente cerca de 65,7% dos casos positivos reais.
  
  •	**AUC-ROC**: 0,895 – sugerindo uma boa capacidade de discriminação entre as classes positiva e negativa.

O modelo teve uma capacidade preditiva boa, visível pela alta acurácia (88,724%) e pelo AUC-ROC elevado, mas a Precisão e o Recall ficaram abaixo do esperado. 

![image](https://github.com/user-attachments/assets/82cd7eec-2ce2-4bed-80c7-b89b6b475943)

### Análisando os Resultados - Tela Predict

O SageMaker possui uma seção chamada “Predict”, onde é possível inserir valores específicos para as variáveis do modelo e obter predições em tempo real com base nos dados fornecidos. 
Iniciamos os testes inserindo dados de atletas que ganharam medalhas nas Olimpíadas de 2024 para validar a capacidade preditiva do modelo. 
Durante as análises, foi confirmado que a coluna NOC teve um impacto significativo nos resultados.
Por exemplo, em um dos testes, foram inseridos os dados de uma atleta brasileira que ganhou medalhas na última Olimpídas, mas o modelo indicou com 92,02% de certeza que a atleta não ganharia medalha. 
No entanto, ao alterar o valor da variável NOC para “USA”, a predição mudou e indicou 60,74% de chances dessa mesma atleta ganhar uma medalha. 
Isso confirma que a variável NOC influencia diretamente as predições, pois essa variável teve 33,685% de impacto no modelo. Nas imagens abaixo é possível ver os testes. 

![image](https://github.com/user-attachments/assets/828298c0-caa1-491d-912a-9ef4833fc489)

![image](https://github.com/user-attachments/assets/babb77fa-e044-4057-a3ea-7e94001cad0e)

### Conclusão

Os resultados obtidos com o modelo treinado no SageMaker indicam um desempenho geral positivo, com uma alta acurácia de 88,724% e uma boa discriminação entre classes, como demonstrado pelo AUC-ROC de 0,895. 
No entanto, identificamos áreas de melhoria, especialmente no equilíbrio entre precisão (60,774%) e recall (65,668%), que ficaram abaixo das expectativas.
A análise revelou que fatores como a variável "NOC" tiveram impacto significativo nos resultados, enquanto as características físicas dos atletas, inicialmente esperadas como relevantes, tiveram menor influência. 
Além disso, a diferença no desempenho entre a previsão das classes "0" (não ganharam medalhas) e "1" (ganharam medalhas) pode estar relacionada ao desequilíbrio no volume de dados que contém uma quantidade 
significativamente maior de atletas que não ganharam medalhas na base utilizada. Essa diferença pode ter direcionado o aprendizado do modelo, tornando-o mais eficaz para prever a classe ("0").
Em geral, o modelo apresenta uma base sólida, mas ajustes futuros e a aplicação de diferentes algoritmos podem melhorar sua capacidade preditiva, garantindo maior equilíbrio e precisão nas predições.


## Análise dos Resultado - Colab

### Avaliação do Modelo nos Dados de Teste

Para avaliar o desempenho do modelo nos dados de teste, utilizamos as métricas AUC, Accuracy e loss:

![image](https://github.com/user-attachments/assets/44f8fa6f-28c2-4e01-a86b-b41a4c6ce266)

**Resultados da Avaliação**:

•	**Loss**: 0.3170

•	**Acurácia**: 0.8834

•	**AUC**: 0.8342

**Interpretação dos Resultados**

•	**Loss**: O valor de loss de 0.3170 é relativamente baixo, indicando que o modelo está se ajustando bem aos dados de teste.

•	**Acurácia**: A acurácia de 88.34% indica que o modelo está correto em aproximadamente 88% das previsões, o que é um bom indicador de performance geral.

•	**AUC**: A AUC de 0.8342 sugere que o modelo tem uma boa capacidade de discriminação entre as classes positivas e negativas. Em termos práticos, isso significa que, em aproximadamente 83% das vezes, o modelo será capaz de distinguir corretamente entre uma classe positiva e uma classe negativa.

## Geração das Previsões com o Modelo

Para avaliar o desempenho do nosso modelo de aprendizado de máquina, seguimos os seguintes passos:

1 - Previsões de Probabilidade: Utilizamos o método predict do modelo para obter as probabilidades preditas para cada amostra no conjunto de teste (X_test). 
Este método retorna a probabilidade de cada amostra pertencer à classe positiva.

2 - Conversão de Probabilidades em Classes: Convertendo as probabilidades em classes binárias (0 ou 1) com um limiar de 0.5. 
Isso significa que se a probabilidade predita for maior ou igual a 0.5, a amostra é classificada como 1 (positiva); caso contrário, é classificada como 0 (negativa).

3 - Definição dos Valores Reais: Garantimos que os valores reais (y_true) estão corretamente definidos a partir do conjunto de teste (y_test). 
Isso é essencial para comparar as previsões do modelo com os valores reais.

4 - Exibição dos Resultados das Previsões: Exibimos os valores reais e as previsões para verificação. 
Isso nos permite visualizar rapidamente como o modelo está performando.

![image](https://github.com/user-attachments/assets/095bbb20-25ec-4ff9-8cef-3567ed716331)

**Interpretação dos Resultados**

Geração das Previsões

Após a geração das previsões com o modelo, observamos os seguintes resultados:

•	Valores Reais: [0, 0, 0, ..., 0, 1, 0]

•	Previsões: [0, 0, 0, ..., 0, 0, 0]

Esses resultados indicam que o modelo foi capaz de prever corretamente a maioria dos casos negativos (0). No entanto, parece que houve algumas dificuldades em prever corretamente os casos positivos (1), 
o que pode ser um ponto a ser melhorado.

## Relatório de Classificação

Para avaliar detalhadamente o desempenho do modelo em cada classe, geramos um relatório de classificação que fornece as métricas de precisão, recall e F1-score para cada classe. 
Utilizamos a função classification_report da biblioteca scikit-learn para isso.

![image](https://github.com/user-attachments/assets/cad61586-5559-4686-9703-511618f38219)

**Interpretação do Relatório de Classificação**

•	Precisão (Precision): A precisão para a classe 0 é 0.90, o que significa que 90% das previsões para a classe 0 são corretas. Para a classe 1, a precisão é 0.68.

•	Recall: O recall para a classe 0 é 0.97, indicando que 97% dos verdadeiros positivos da classe 0 foram corretamente identificados. Para a classe 1, o recall é 0.40, 
o que sugere que o modelo tem dificuldade em identificar todos os verdadeiros positivos da classe 1.

•	F1-Score: O F1-score é a média harmônica entre precisão e recall. Para a classe 0, o F1-score é 0.93, e para a classe 1, é 0.50.

•	Suporte (Support): O suporte indica o número de ocorrências reais de cada classe no conjunto de dados. No caso, há 34,650 instâncias da classe 0 e 6,018 da classe 1.


## Matriz de Confusão

Para entender melhor o desempenho do modelo, geramos a matriz de confusão, que exibe o número de verdadeiros positivos, verdadeiros negativos, falsos positivos e falsos negativos.

**Interpretação da Matriz de Confusão**

•	Verdadeiros Negativos (VN): 33,519 - O número de instâncias negativas corretamente classificadas como negativas.

•	Falsos Positivos (FP): 1,131 - O número de instâncias negativas incorretamente classificadas como positivas.

•	Falsos Negativos (FN): 3,610 - O número de instâncias positivas incorretamente classificadas como negativas.

•	Verdadeiros Positivos (VP): 2,408 - O número de instâncias positivas corretamente classificadas como positivas.


## Conclusão

A matriz de confusão revela que o modelo tem um bom desempenho na classificação das instâncias negativas, com um alto número de verdadeiros negativos (33,519) e um número relativamente baixo de falsos positivos (1,131). 
No entanto, o modelo apresenta dificuldades na classificação das instâncias positivas, com um número significativo de falsos negativos (3,610), o que indica que muitas instâncias positivas estão sendo classificadas 
incorretamente como negativas.
Esses resultados sugerem que, embora o modelo tenha uma boa acurácia geral, há espaço para melhorias na detecção de instâncias positivas. Técnicas como ajuste de limiar, 
balanceamento de classes ou uso de algoritmos mais sofisticados podem ser exploradas para melhorar o desempenho do modelo na classificação de instâncias positivas.




