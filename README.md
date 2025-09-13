# MVP3-COVID19-ML

🧬 Predição de Óbitos em Pacientes com COVID-19

Este projeto tem como objetivo desenvolver e avaliar modelos de classificação supervisionada para prever a probabilidade de óbito em pacientes com COVID-19, utilizando um dataset público com informações clínicas e demográficas.

O trabalho envolve desde a exploração dos dados, passando pelo pré-processamento e balanceamento de classes, até a seleção e otimização de algoritmos de machine learning, com foco principal no Gradient Boosting Classifier (GBM).

📂 Estrutura do Projeto
├── data/                # Dados brutos e/ou processados
├── notebooks/           # Notebooks com exploração, modelagem e análises
├── models/              # Modelos treinados (.pkl)
├── src/                 # Scripts Python organizados (pré-processamento, treino, avaliação)
├── README.md            # Documentação do projeto
└── requirements.txt     # Dependências do projeto

🚀 Tecnologias Utilizadas

Python 3.10+

Bibliotecas principais:

pandas, numpy

scikit-learn

matplotlib, seaborn

imbalanced-learn (para balanceamento)

joblib (para salvar/carregar modelos)

📊 Etapas do Projeto

Exploração do Dataset

Análise das variáveis clínicas e demográficas.

Identificação de desbalanceamento de classes.

Pré-processamento

Criação do rótulo (died).

Conversão de variáveis binárias para booleanas.

Agrupamento de faixas etárias.

Balanceamento de Classes

Aplicação de undersampling para reduzir o viés do modelo.

Modelagem

Teste inicial com 7 algoritmos de classificação (LR, KNN, CART, NB, RF, GBM, ADA).

Comparação de métricas: acurácia, f1-score e matriz de confusão.

Seleção do GBM como melhor modelo.

Otimização de Hiperparâmetros

Aplicação de GridSearchCV.

Melhores parâmetros identificados:

{
  "learning_rate": 0.1,
  "max_depth": 4,
  "max_features": "sqrt",
  "n_estimators": 300,
  "subsample": 1.0
}


Avaliação Final

Accuracy Teste: ~0.916

F1-score Teste: ~0.919

Modelo equilibrado entre classes, sem tendência de prever apenas a classe majoritária.

Exportação do Modelo

O modelo final foi treinado em todos os dados e salvo em .pkl para uso futuro.

📈 Resultados

O Gradient Boosting apresentou o melhor desempenho em termos de acurácia e f1-score.

O balanceamento de classes foi essencial para melhorar a performance.

O modelo mostrou boa capacidade preditiva, mas deve ser usado como suporte e não substituto de decisões médicas.

⚠️ Limitações

O modelo depende da qualidade e representatividade dos dados.

Não é 100% confiável: deve ser interpretado como ferramenta auxiliar.

O comportamento da pandemia pode mudar (novas variantes, protocolos, vacinas), afetando a performance.

🔮 Trabalhos Futuros

Testar técnicas de oversampling (ex: SMOTE) e ensembles balanceados.

Explorar métodos de interpretação de modelos (SHAP, LIME).

Validar o modelo em datasets de diferentes regiões.

Desenvolver API/Dashboard para aplicação prática em hospitais.

📦 Como Executar o Projeto

Clone este repositório:

git clone https://github.com/seu-usuario/covid-prediction.git
cd covid-prediction


Crie e ative um ambiente virtual:

python -m venv venv
source venv/bin/activate   # Linux/Mac
venv\Scripts\activate      # Windows


Instale as dependências:

pip install -r requirements.txt


Execute os notebooks ou scripts na pasta src/.

📌 Uso do Modelo Treinado
import joblib
import pandas as pd

# Carregar pipeline salvo
pipeline = joblib.load("models/gbm_final_model.pkl")

# Fazer predição em novos dados
novos_dados = pd.DataFrame([...])  # mesmo formato do dataset original
pred = pipeline.predict(novos_dados)
prob = pipeline.predict_proba(novos_dados)

✒️ Autor

Edu – Analista de Dados 👨‍💻
