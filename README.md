![Status](https://img.shields.io/badge/status-concluído-brightgreen)

# 📊 Análise Preditiva de Evasão de Clientes (Churn)

Este projeto realiza uma análise completa sobre a evasão de clientes (churn) em uma empresa de telecomunicações. O objetivo é não apenas construir um modelo de machine learning para prever quais clientes têm maior probabilidade de sair, mas também extrair **insights acionáveis** para fundamentar estratégias de retenção.

## 🎯 Objetivos Estratégicos

* **Diagnosticar:** Identificar os principais fatores demográficos, de consumo e de contrato que influenciam a decisão de um cliente em deixar a empresa.
* **Prever:** Desenvolver e comparar modelos de classificação (Regressão Logística e Random Forest) para prever o churn com alta acurácia e recall.
* **Agir:** Traduzir os resultados do modelo em recomendações de negócio claras e práticas para reduzir a taxa de evasão.

## 🧠 Metodologia e Modelagem

O fluxo do projeto seguiu as seguintes etapas:

1.  **Pré-processamento de Dados:**
    * **Encoding:** Conversão de variáveis categóricas em formato numérico para que pudessem ser utilizadas pelos modelos.
    * **Normalização:** Aplicação de `StandardScaler` nos dados para o modelo de Regressão Logística, garantindo que as variáveis com diferentes escalas tivessem o mesmo peso.
    * **Balanceamento de Classes:** Uso da técnica **SMOTE** (`Synthetic Minority Over-sampling Technique`) para criar exemplos sintéticos da classe minoritária (clientes que evadiram), corrigindo o desequilíbrio natural dos dados e evitando que o modelo se tornasse enviesado para a classe majoritária.

2.  **Modelos Preditivos:**
    * **Regressão Logística:** Escolhido por sua alta interpretabilidade. Os coeficientes do modelo nos permitem entender o peso e a direção (positiva ou negativa) da influência de cada variável no churn.
    * **Random Forest:** Um modelo de conjunto (ensemble) robusto, escolhido por sua capacidade de capturar relações não-lineares complexas entre as variáveis e sua resistência a overfitting.

## 📈 Resultados e Insights

### Métricas de Desempenho
A tabela abaixo compara o desempenho dos dois modelos após o balanceamento com SMOTE e ajuste de hiperparâmetros.

| Modelo                      | Acurácia | Precisão | Recall | F1-score |
| --------------------------- | -------- | -------- | ------ | -------- |
| Regressão Logística (SMOTE) | 0.7611   | 0.5287   | **0.6578** | 0.5862   |
| Random Forest (SMOTE)       | **0.7652** | **0.5375** | 0.6257 | 0.5783   |

**Interpretação:** Ambos os modelos são competitivos. A **Regressão Logística** se destaca no **Recall**, o que é crucial para este problema de negócio: é preferível contatar um cliente que não iria sair (falso positivo) do que deixar de agir sobre um cliente que realmente vai sair (falso negativo). O **Random Forest** oferece uma precisão ligeiramente maior.

### Fatores Chave de Churn

🔥 **O que AUMENTA o Churn?**
* **Contrato Mensal:** Clientes sem vínculo de longo prazo são os mais propensos a sair.
* **Baixo Tempo de Serviço:** Clientes novos (poucos meses) ainda não estabeleceram lealdade.
* **Internet de Fibra Óptica:** Embora seja um serviço premium, pode estar associado a custos mais altos ou problemas técnicos iniciais que geram insatisfação.
* **Encargos Mensais Elevados:** Um alto custo mensal é um forte motivador para a busca de alternativas.

❄️ **O que REDUZ o Churn (Fatores de Retenção)?**
* **Contrato de Longo Prazo (Um ou dois anos):** O compromisso contratual é o fator mais forte de retenção.
* **Alto Tempo de Serviço:** Clientes antigos tendem a ser mais leais.
* **Dependentes e Parceiros:** Clientes com famílias associadas ao plano demonstram um maior "custo de mudança".
* **Serviços Adicionais:** Uso de backup online, seguro de dispositivo e suporte técnico estão associados a menor churn.

## 💡 Recomendações e Ações Estratégicas

Com base nos insights, as seguintes ações podem ser implementadas:

1.  **Para Clientes com Contrato Mensal:** Criar campanhas proativas oferecendo descontos ou benefícios para a migração para contratos anuais ou bienais.
2.  **Para Clientes Novos (baixo tempo de serviço):** Implementar um programa de *onboarding* nos primeiros 3 meses, com acompanhamento personalizado para garantir a satisfação e tirar dúvidas.
3.  **Para Clientes de Fibra Óptica:** Monitorar a qualidade do serviço de perto e oferecer um canal de suporte técnico prioritário para esse segmento.
4.  **Ofertas Personalizadas:** Usar o modelo para gerar uma "pontuação de risco de churn" semanal. Clientes com alta pontuação devem ser alvo de ações de retenção, como ofertas de desconto nos encargos mensais ou pacotes de serviços adicionais.

## 🚀 Próximos Passos

* **Testar modelos mais complexos:** Implementar Gradient Boosting (XGBoost, LightGBM) para buscar ganhos de performance.
* **Engenharia de Features:** Criar novas variáveis, como a razão entre o encargo mensal e o tempo de serviço.
* **Dashboard Interativo:** Desenvolver um painel em Power BI ou Streamlit para que a área de negócio possa simular cenários e consultar o risco de churn de clientes específicos.

## 💻 Tecnologias Utilizadas

* **Linguagem:** Python 3
* **Bibliotecas de Análise:** pandas, numpy
* **Bibliotecas de Visualização:** matplotlib, seaborn
* **Bibliotecas de Machine Learning:** scikit-learn, imblearn
