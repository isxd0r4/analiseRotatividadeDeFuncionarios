# Análise de Rotatividade de Funcionários - IBM HR Analyytics
Este repositório contém um projeto voltado para o setor de Recursos Humanos (People Analytics). O objetivo é prever a evasão de funcionários (Attrition) utilizando o conjunto de dados IBM HR Analytics Employee Attrition & Perfomance, identificando padrões que levam colaboradores a deixarem a empresa.

## Objetivo do projeto
O foco principal é a identificação proativa de funcionários com risco de saída. Para este problema, a métrica de Recall foi priorizada, uma vez que para o RH é mais custoso não identificar um funcionário que pretende sair (Falso Negativo) do que investigar um funcionário que prentedia ficar (Falso Positivo).

## Tecnologias e bibliotecas utilizadas
* **Ambiente:** Google Colab
* **Linguagem:** Python
* **Visualização de dados:** `matplolib`, `seaborn`
* **Manipulação de dados:** `pandas`
* **Aprendizado de máquina:** `scikit-learn` (Logistic Regression, Random Forest)

## Metodologia
O fluxo de trabalho foi dividido nas seguintes etapas:
1. **Aquisição de dados:** Download do dataset via API do Kaggle e renomeação do arquivo para facilitar acesso
2. **Análise exploratória visual:** Geração de gráficos de contagem relacionados a evasão com váriaveis críticas (`OverTime`, `YearsAtCompany` e `DistanceFromHome`)
3. Engenharia de dados e pré-processamento:
  * Remoção de colunas irrelevantes (`EmployeeCount`, `StandardHours`, etc.)
  * Conversão da variável alvo para formato binário (0 e 1)
  * Aplicação de *One-Hot Enconding* para transformar variáveis categóricas em numéricas
  * Tratamento de desbalanceamento de classes utilizando o parâmetro `class_weight = 'balanced'` nos modelos
  * Padronização de escala com `StandardScaler`
4. **Modelagem e otimização:** Implementação de `GridSearchCV` para busca dos melhores hiperparâmetros
  * Uso de validação cruzada (K-Fold CV = 5) para garantir a estabilidade dos resultados
5. **Avaliação:** Comparação entre Regressão Logística e Random Forest atravpes do `classification_report`

## Como executar no Google Colab
Este notebook foi estruturado para execução direta no ambiente do Google Colab:

### Passo 01: Carregamento
1. Acesse o [Google Colab](https://colab.research.google.com/)
2. Import o arquivo `.ipynb` através da aba Upload

### Passo 02: Execução
1. Vá até o menu **Runtime** (Ambiente de execução) e selecione **Run All** (Executar tudo)
2. O Código baixará automaticamente o dataset, processará as informações e exibirá os gráficos e métricas de desempenho

## Considerações finais
Observou-se que os resultados obtidos ainda não atingiram o nível de performance desejado para uma implementação em produção. A detecção de evasão apresentou desafios devido ao desbalaceamento original dos dados e à complexidade das relações entre as variáveis. Dessa forma, o estudo e aplicação de melhorias nos modelos e nas técnicas utilizadas permanecem como propostas para trabalhos futuros, visando aprimorar o desempenho preditivo e a capacidade de generalização da solução.
