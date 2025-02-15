
---

# Projeto de Mineração de Dados: Previsão de Sobrevivência de Cavalos

## Introdução
Este projeto tem como objetivo desenvolver um modelo de classificação supervisionado para prever a sobrevivência de cavalos com base em seu histórico médico. O dataset utilizado contém 27 atributos (numéricos e categóricos) que descrevem as condições de saúde dos cavalos e 3 classes de saída: **sobreviveu**, **morreu** ou **foi submetido à eutanásia**.

O trabalho foi desenvolvido por:
- Alexandre Koury
- Fabio Faria
- Lara Teixeira
- Matheus Bernardes
- Pedro Bethencourt

## Metodologia
O projeto foi dividido nas seguintes etapas:

1. **Análise Exploratória de Dados (EDA)**:
   - Verificação das dimensões dos datasets de treino e teste.
   - Identificação de atributos numéricos e categóricos.
   - Análise de valores faltantes e correlação entre atributos.
   - Teste de Qui-Quadrado para identificar a significância dos atributos categóricos em relação à variável alvo (`outcome`).
   - Verificação do balanceamento das classes de saída.

2. **Pré-processamento**:
   - Remoção de atributos irrelevantes ou com alta correlação.
   - Tratamento de valores faltantes: preenchimento de valores numéricos com a mediana e valores categóricos com a moda.
   - Normalização dos atributos numéricos usando `RobustScaler`.
   - Codificação de atributos categóricos: `Label Encoding` para atributos ordinais e `Dummy Encoding` para atributos nominais.
   - Balanceamento das classes de saída usando **undersampling** e **oversampling** (SMOTE).

3. **Modelagem e Treinamento**:
   - Foram testados quatro algoritmos de classificação:
     - **Random Forest (RF)**
     - **Logistic Regression (LR)**
     - **Support Vector Machine (SVM)**
     - **K-Nearest Neighbors (KNN)**
   - Cada modelo foi treinado e validado em três cenários: base desbalanceada, base com undersampling e base com oversampling.
   - Validação cruzada com 5 folds para avaliar o desempenho dos modelos.

4. **Avaliação dos Modelos**:
   - Métricas utilizadas: **Acurácia**, **Coeficiente Kappa** e **F1-Score**.
   - Análise de overfitting usando o **Out-of-Bag Score** (OOB) para modelos Random Forest.
   - Matriz de confusão para avaliar a qualidade das previsões.

## Resultados
- **Random Forest** apresentou o melhor desempenho geral, com acurácia média de **87%** na base com oversampling.
- **KNN** e **SVM** também tiveram resultados satisfatórios, com F1-Score de **0.88** e **0.81**, respectivamente.
- O modelo **Random Forest** mostrou sinais de overfitting na base desbalanceada, mas teve desempenho mais equilibrado na base com oversampling.
- O modelo **KNN com oversampling** foi escolhido como uma alternativa segura, com menos erros críticos (prever sobrevivência quando o cavalo morreu ou foi submetido à eutanásia).

## Conclusão
O modelo **Random Forest** foi o que apresentou o melhor desempenho geral, mas há indícios de overfitting. Como alternativa, o modelo **KNN com oversampling** pode ser uma escolha mais segura, especialmente para evitar erros críticos na previsão de sobrevivência.

Para melhorar a robustez do modelo, sugere-se:
- Calibração de probabilidades.
- Rejeição de classe.
- Uso de ensemble de modelos.
- Avaliação de especialistas para casos críticos.

## Como Executar o Projeto
1. Clone o repositório:
   ```bash
   git clone https://github.com/matheusbnas/projeto_dataMining_puc.git
   cd projeto_dataMining_puc/notebook
   ```

2. Instale as dependências:
   ```bash
   pip install -r requirements.txt
   ```

3. Execute o Jupyter Notebook:
   ```bash
   jupyter notebook Trabalho_DM_classificacao.ipynb
   ```

## Dependências
As principais bibliotecas utilizadas foram:
- `pandas`
- `numpy`
- `scikit-learn`
- `matplotlib`
- `seaborn`
- `imblearn` (SMOTE)

## Licença
Este projeto está licenciado sob a licença MIT. Consulte o arquivo [LICENSE](https://opensource.org/license/mit) para mais detalhes.

---

Este `README.md` resume o projeto de forma clara e direta, destacando os principais pontos e resultados.
