# Etapa 4 - APRENDIZAGEM DE MÁQUINA

Nesta etapa, após a seleção das ferramentas e a preparação dos dados, o objetivo é explorar e aplicar diversas abordagens de aprendizado de máquina. 

A equipe conduziu experimentos com diferentes ferramentas e algoritmos, buscando compará-los para identificar aquele que oferece o melhor desempenho e traz mais conhecimento para o problema em questão. 

Para tanto, foi necessário alterar a etapa de pré-processamento de dados, que haviam sido preparados na perspectiva de visualização de dados e não aprendizado de máquina.

## Aprendizado de Máquina com Python

O script python produzido nessa etapa pode ser encontrado neste projeto na pasara scripts/PreverOlimpiada_athlete_events.ipynb

###  Importação de Bibliotecas e Carregamento Inicial

Inicialmente, são baixadas algumas bibliotecas, pacotes e funções que serão utilizadas no pré-processamento dos dados e na aplicação dos modelos de Machine Learning: 
Pandas, Numpy, Matplotlib, Seaborn, Sklearn e TensorFlow.

![image](https://github.com/user-attachments/assets/b53d7ed7-6466-4ad8-97f9-abd6cc35deb6)

Os dados são carregados e a função .info() é aplicada para obter uma visão geral, identificando que as colunas Age, Height, Weight e Medal possuem valores nulos que precisam ser tratados.

![image](https://github.com/user-attachments/assets/0501eaca-0e25-433c-b9f7-f7d940ad5f0c)

![image](https://github.com/user-attachments/assets/64364abe-5670-4f93-85ae-bda63aa81e70)

![image](https://github.com/user-attachments/assets/2beccc69-4c21-401f-b269-64327dd8ba8e)

### Ajuste da Coluna Medalhas

Para prever se o atleta ganhará uma medalha (independentemente do tipo), os valores categóricos na coluna Medal são substituídos por 0 (sem medalha) ou 1 (com medalha). 

Utiliza-se a função lambda para isso:

![image](https://github.com/user-attachments/assets/50bf3384-25c3-406a-82b8-a2f6d5ac6f82)

### Limpeza de Dados

São retiradas as colunas ID, Name, Games e NOC, pois são desnecessárias para a aplicação do modelo de Machine Learning:

![image](https://github.com/user-attachments/assets/3a1fcbd2-6b2b-4f15-9e06-bf4b65feb4f1)

Para identificar dados faltantes, são aplicadas as funções .isna(), .sum() e .mean():

![image](https://github.com/user-attachments/assets/c0c9e5e7-f2d3-429c-9089-28a865bb1fef)

![image](https://github.com/user-attachments/assets/a5021afe-4fc9-4141-b345-2e674e603c07)

Para completar os registros faltantes, a média de idade, altura e peso dos atletas (agrupados pelo sexo) é incluída nos casos em que essas informações estão ausentes:

![image](https://github.com/user-attachments/assets/a0024942-10b1-4061-9573-32423f633b58)

Checa-se o resultado:

![image](https://github.com/user-attachments/assets/71cd32de-65b9-45f1-b4f2-4a494f871492)

Conforme verificado, não há mais valores nulos no DataFrame.

Gerou-se um arquivo CSV com os dados transformados:

![image](https://github.com/user-attachments/assets/cf1dfa8a-1523-4434-9652-a4ebb643c92c)


### Codificação dos Dados

A fase de codificação dos dados transforma colunas categóricas em variáveis binárias (0 e 1) e aplica a codificação one-hot para colunas adicionais. A função binary_encode é utilizada para as colunas Sex e Season:

![image](https://github.com/user-attachments/assets/4b862931-292a-4d8c-9a9a-33ac60db34aa)

Para colunas como Team, City, Sport e Event, a função onehot_encode é aplicada para criar variáveis dummies:

![image](https://github.com/user-attachments/assets/9ee0db32-f8eb-4628-825c-0b11bdd1c096)

Visualização dos dados codificados:

![image](https://github.com/user-attachments/assets/5eadb0d1-f9c0-4410-9f53-e8f8d815c85b)

![image](https://github.com/user-attachments/assets/40ce2199-6403-4e0c-a3a7-64921d484098)

Verificar se ainda existem colunas não numéricas no DataFrame:

![image](https://github.com/user-attachments/assets/758a485c-ed4a-4689-a7c8-482131275541)

### Visualização de Correlações

Uma matriz de correlação é gerada e visualizada em um mapa de calor para identificar variáveis fortemente correlacionadas, para entender padrões nos dados e ajudar na seleção de características para modelagem:

![image](https://github.com/user-attachments/assets/dab8738b-8362-439d-a4dd-7f06693e6ada)

![image](https://github.com/user-attachments/assets/0d314bf4-87e2-4af7-bb05-24a2dc9aec46)

### Preparação dos Dados para o Modelo de Machine Learning

Uma amostra dos dados é separada e a variável alvo (y) e as variáveis de entrada (X) são definidas. A normalização das características é realizada utilizando StandardScaler:

![image](https://github.com/user-attachments/assets/480b7429-8078-41ff-ac22-cfdb92d8ac6d)

Os dados são então divididos em conjuntos de treino e teste para avaliar a acurácia do modelo, O parâmetro “random_state” permite que os mesmos números aleatórios sejam gerados toda vez que o código for executado:

![image](https://github.com/user-attachments/assets/06b0d817-59fd-4e9c-ae1e-471b5a0fe898)


### Treinamento do Modelo com TensorFlow e Keras

Configurou-se a rede neural para que a camada de entrada utilize a quantidade de características de X.shape[1]. Esse termo representa o número de colunas em X, correspondente à quantidade de características (ou variáveis) que cada amostra possui.

![image](https://github.com/user-attachments/assets/ee3e8dad-4bbe-4279-a74a-bedd615b100f)

Criaram-se mais duas camadas densas (totalmente conectadas), cada uma com 64 neurônios e utilizando a função de ativação ReLU. Essas camadas são adicionadas sequencialmente, permitindo que a rede aprenda padrões e relações complexas nos dados ao processar as informações de forma gradual. As camadas densas são as seguintes:

![image](https://github.com/user-attachments/assets/1b7f0ead-f48d-488d-bd09-89ead261b9d2)

Criou-se a camada de saída, que contém apenas um neurônio, pois, sendo um problema de classificação binária, deseja-se uma única saída que represente a probabilidade de uma amostra pertencer a uma das duas classes. O valor produzido por esse neurônio será uma probabilidade entre 0 e 1. A camada de saída é a seguinte:

![image](https://github.com/user-attachments/assets/bc97d01b-7ae5-4bc1-9c56-e87b10e81f5e)

Gera-se o modelo de rede neural, conectando a camada de entrada com a camada de saída:

![image](https://github.com/user-attachments/assets/314ddd21-01ae-4809-814e-2395c04adfdc)

Iniciou-se a compilação do modelo, utilizando o otimizador Adam, que ajusta automaticamente a taxa de aprendizado ao longo do treinamento. Aplicou-se a função de perda binary_crossentropy, com o objetivo de minimizar a perda durante o treinamento, ajustando os pesos do modelo para aprimorar a precisão das previsões. Foram adotadas métricas de avaliação (accuracy e AUC) para monitorar o desempenho. O código da compilação do modelo é o seguinte:

![image](https://github.com/user-attachments/assets/1725c08a-7ec9-470c-9f48-88ec99311d57)

Realizou-se o treinamento do modelo, iniciando pela divisão dos dados (X_train e y_train, com validation_split=0.2), onde 20% dos dados são utilizados para validação durante o treinamento, enquanto os 80% restantes servem para o treinamento do modelo. 

Configurou-se o tamanho do lote (batch_size=32), o que significa que os pesos do modelo serão atualizados após cada lote de 32 amostras. Definiu-se o número de épocas (epochs=100), que representa o número máximo de passagens pelo conjunto de treinamento completo. 

Adicionou-se um callback com parâmetros de monitoramento (val_loss) para observar a perda de validação ao longo das épocas; de patience=3 para que o treinamento seja interrompido se não houver melhoria na perda de validação por 3 épocas consecutivas; e de restore_best_weights=True para garantir que os pesos do modelo sejam restaurados para os melhores encontrados durante o treinamento. 

O código do treinamento do modelo é o seguinte:

![image](https://github.com/user-attachments/assets/62ff788c-dff0-4e16-918c-446c1c3ec90b)

Teve-se como saída o código abaixo, que demonstra o progresso do treinamento do modelo ao longo das épocas, detalhando diversas métricas de desempenho:

![image](https://github.com/user-attachments/assets/c05b809b-ec1a-4426-821e-d75b3002efcb)

Os resultados serão analizados na próxima etapa.


## Aprendizado de Máquina com o SageMaker

Para complementar o modelo com as bibliotecas Python, utilizou-se o Amazon SageMaker Studio, um ambiente de desenvolvimento integrado (IDE) para *machine learning* que facilita a construção, o treinamento e a implantação de modelos de aprendizado de máquina na nuvem.

### Criação do Domínio e Configuração do Ambiente

Configurou-se o domínio do SageMaker utilizando a opção de configuração rápida para acessar o Studio. 

Usando a opção de AutoML, que treina o modelo automaticamente no SageMaker Canvas, realizou-se a importação dos dados já armazenados no Amazon S3. Não foram realizadas transformações, pois essas já haviam sido executadas com o script Python.

![image](https://github.com/user-attachments/assets/8c2d0715-73ef-4059-a686-7774eda19182)

![image](https://github.com/user-attachments/assets/45ba3620-99d2-4406-9a2e-04ccc99f34dc)

![image](https://github.com/user-attachments/assets/3ac42279-7d9d-41bc-b427-bb87b1e4b0de)

### Criação do modelo 

Após o upload dos dados, iniciou-se a criação do modelo, escolhendo qual coluna se desejava prever. Para este estudo, decidiu-se prever a coluna de medalhas dos atletas, utilizando um modelo de duas categorias. Nesse modelo, a previsão será se o atleta ganharia ou não uma medalha.

![image](https://github.com/user-attachments/assets/8a58317d-e240-4f19-87fe-4b7980330ddc)

O Amazon SageMaker Autopilot utiliza uma variedade de modelos e algoritmos de aprendizado de máquina para otimizar o desempenho e gerar o melhor modelo possível para cada conjunto de dados. O Autopilot executa um pipeline automatizado que abrange várias etapas, como seleção de recursos e ajuste de hiperparâmetros, empregando uma combinação de algoritmos. Os principais modelos de machine learning no SageMaker Autopilot incluem: XGBoost, Redes Neurais Profundas, Regressão Linear, Random Forests e Árvores de Decisão.

Para uma predição binária (previsão de duas categorias), o Autopilot no SageMaker frequentemente utiliza XGBoost, regressão logística e redes neurais como opções principais. Ele testa e compara esses algoritmos para identificar o melhor modelo, além de realizar ajustes automáticos em hiperparâmetros para otimizar a acurácia do modelo final. No entanto, não é possível afirmar qual desses modelos foi exatamente utilizado neste estudo.

![image](https://github.com/user-attachments/assets/1fdf4b65-0c3b-43eb-82cf-a9fc9f4fff25)

Os resultados serão analizados na próxima etapa.
