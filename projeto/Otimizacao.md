# Etapa 6 - Otimização

## Conclusão do Projeto

Neste projeto, utilizamos técnicas de aprendizado de máquina para prever determinados resultados com base em um conjunto de dados restrito. A seguir, destacamos os principais pontos de atenção e sugestões de melhorias para futuros trabalhos.

## Pontos de Atenção

1. **Limitação de Memória**:
   - Devido à restrição de RAM no Google Colab, utilizamos apenas 30% da amostra disponível. Essa limitação de memória impactou a capacidade de processamento e a representatividade dos dados, potencialmente afetando a precisão dos modelos.

2. **Desequilíbrio entre Classes**:
   - O conjunto de dados apresentava um desequilíbrio significativo entre as classes, com poucos medalhistas na base. Esse desequilíbrio dificultou as previsões para determinadas classes.
   - Além disso, os dados restritos (altura, peso, sexo, país, esporte e evento) reduziram o contexto disponível para o modelo, limitando sua capacidade de fazer previsões precisas.

3. **Resultados do Modelo**:
   - O modelo apresentou excelente desempenho na classificação de instâncias negativas, com 33.519 verdadeiros negativos (TN) e apenas 1.131 falsos positivos (FP).
   - No entanto, a alta taxa de falsos negativos (3.610 FN) prejudicou a detecção de instâncias positivas, indicando uma necessidade de melhorias na identificação de casos positivos.

4. **Limitação ao Uso do SageMaker**:
   - O Amazon SageMaker é uma ferramenta poderosa para treinamento e implantação de modelos de aprendizado de máquina, mas é uma solução paga. Essa limitação financeira restringiu o uso contínuo e a escalabilidade do projeto.

## Melhorias Sugeridas

1. **Aumento da Capacidade de Memória**:
   - Com mais memória disponível, poderíamos trabalhar com 100% dos dados, o que geraria modelos mais confiáveis e representativos. Isso permitiria uma análise mais completa e precisa dos dados.

2. **Incorporação de Outras Bases de Dados**:
   - Incorporar outras bases de dados com mais características de atletas e resultados aumentaria a qualidade e a diversidade dos registros. Isso forneceria um contexto mais rico para o modelo, potencialmente melhorando sua precisão.

3. **Exploração de Outras Abordagens**:
   - Estudar e testar outras abordagens, utilizando diferentes algoritmos e modelos preditivos, pode levar a melhorias significativas no desempenho do modelo. Técnicas como Gradient Boosting, Random Forest e redes neurais profundas podem ser exploradas.

4. **Treinamento Separado de Datasets**:
   - Treinar separadamente os datasets com registros de quem ganhou medalhas e quem não ganhou pode ajudar a entender melhor o comportamento dos modelos em diferentes cenários. Isso pode revelar padrões específicos que podem ser utilizados para melhorar as previsões.

## Considerações Finais

Este projeto demonstrou a viabilidade do uso de aprendizado de máquina para previsões baseadas em dados esportivos, apesar das limitações enfrentadas. As melhorias propostas oferecem uma opção interessante para futuras iterações do projeto, com o objetivo de aprimorar tanto a precisão quanto a confiabilidade dos modelos preditivos.
