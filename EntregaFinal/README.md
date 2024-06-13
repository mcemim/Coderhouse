# Documento Executivo

## Tabela de Conteúdos

1. [Descrição do caso de negócio](#descrição-do-caso-de-negócio)
2. [Tabela de versionamento](#tabela-de-versionamento)
3. [Objetivos do modelo](#objetivos-do-modelo)
4. [Descrição dos dados a partir da perspectiva do Negócio](#descrição-dos-dados-a-partir-da-perspectiva-do-negócio)
5. [Resultados encontrados pela EDA](#resultados-encontrados-pela-eda)
6. [Algoritmo Escolhido](#algoritmo-escolhido)
7. [Métricas de Desempenho do Modelo](#métricas-de-desempenho-do-modelo)
8. [Iterações de Otimização](#iterações-de-otimização)
9. [Métricas finais do Modelo Otimizado](#métricas-finais-do-modelo-otimizado)
10. [Linhas de ações futuras](#linhas-de-ações-futuras)
11. [Conclusões](#conclusões)

## Descrição do caso de negócio

O contexto gira em torno da dinâmica das reservas de hotéis feitas por meio de canais online. Com a popularização desses canais, as opções de reserva e o comportamento dos clientes mudaram significativamente. No entanto, um desafio enfrentado pelos hotéis é o alto número de cancelamentos ou não comparecimentos nas reservas.

Esses cancelamentos podem ocorrer por uma variedade de motivos, como mudanças de planos ou conflitos de agenda, muitas vezes facilitados pela opção de cancelamento gratuito ou de baixo custo oferecida aos clientes. Embora isso possa ser conveniente para os hóspedes, para os hotéis representa uma questão menos favorável, podendo diminuir a receita esperada.

Diante dessa situação, a pergunta chave é se é possível prever se um cliente vai honrar a reserva feita ou se irá cancelá-la. Essa previsão poderia ajudar os hotéis a melhor gerenciar suas operações e minimizar os impactos negativos dos cancelamentos em sua receita e operações.

## Tabela de versionamento

| Versão | Data       | Descrição                                 |
|--------|------------|-------------------------------------------|
| 1.0    | 2024-04-09 | Adicionada entrega 01 no repositório      |
| 2.0    | 2024-04-23 | Adicionada entrega 03 no repositório      |
| 3.0    | 2024-06-13 | Adicionada entrega final no repositório   |

## Objetivos do modelo

O objetivo principal do modelo é prever se um cliente vai honrar a reserva feita ou se irá cancelá-la. Os objetivos secundários incluem:
- Melhorar a gestão operacional dos hotéis.
- Minimizar os impactos negativos dos cancelamentos na receita dos hotéis.
- Auxiliar na tomada de decisão para estratégias de overbooking.

## Descrição dos dados a partir da perspectiva do Negócio

### Temática
O banco de dados utilizado trata das reservas de hotéis, incluindo informações sobre os clientes, detalhes das reservas e o status das mesmas (cancelada ou honrada).

### Variáveis Selecionadas
As principais variáveis selecionadas incluem:
- **Data da reserva**: data em que a reserva foi feita.
- **Data de check-in**: data prevista para o check-in.
- **Duração da estadia**: número de dias entre check-in e check-out.
- **Número de hóspedes**: número de pessoas incluídas na reserva.
- **Preço total da reserva**: custo total da estadia.
- **Método de pagamento**: tipo de pagamento utilizado.
- **Política de cancelamento**: regras de cancelamento aplicáveis à reserva.

### Segmentação dos Registros
Os registros foram segmentados com base no status da reserva (cancelada ou honrada).

### Decisões Tomadas para Chegar ao Dataset
Para preparar o dataset final, foram realizadas as seguintes etapas:
- **Limpeza de dados**: remoção de registros com informações inconsistentes ou faltantes.
- **Tratamento de missing values**: substituição ou exclusão de valores ausentes.
- **Transformação de variáveis**: normalização e codificação de variáveis categóricas.

## Resultados encontrados pela EDA

Os resultados da Análise Exploratória dos Dados (EDA) estão descritos em uma apresentação. [Link para a apresentação](https://docs.google.com/presentation/d/e/2PACX-1vQNt1RnUiJ4menCyF2dg0i-A4lBF8pZrx24fstYzNvrC7zd-QQCV-jYsc8xYKyOBibMhtSCZJv6uCuT/pub?start=false&loop=false&delayms=60000)

## Algoritmo Escolhido

### Random Forest
O algoritmo Random Forest foi escolhido devido à sua capacidade de lidar com grandes volumes de dados e alta dimensionalidade, além de ser robusto contra overfitting. O Random Forest utiliza um conjunto de árvores de decisão para melhorar a precisão e estabilidade das previsões.

### Decision Tree
O algoritmo Decision Tree foi selecionado por sua simplicidade e interpretabilidade. As árvores de decisão são fáceis de entender e interpretar, o que é útil para explicar as previsões aos stakeholders.

### K-Nearest Neighbors (KNN)
O KNN foi escolhido por sua simplicidade e eficácia em problemas de classificação. Ele classifica os pontos de dados com base na classe majoritária dos seus vizinhos mais próximos.

## Métricas de Desempenho do Modelo

### Árvore de Decisão
|              | Precision | Recall | F1-score | Support |
|--------------|-----------|--------|----------|---------|
| Classe 0     | 0.79      | 0.81   | 0.80     | 3607    |
| Classe 1     | 0.90      | 0.90   | 0.90     | 7276    |
| Accuracy     |           |        | 0.87     | 10883   |
| Macro avg    | 0.85      | 0.85   | 0.85     | 10883   |
| Weighted avg | 0.87      | 0.87   | 0.87     | 10883   |

### KNN
|              | Precision | Recall | F1-score | Support |
|--------------|-----------|--------|----------|---------|
| Classe 0     | 0.75      | 0.63   | 0.68     | 3607    |
| Classe 1     | 0.83      | 0.90   | 0.86     | 7276    |
| Accuracy     |           |        | 0.81     | 10883   |
| Macro avg    | 0.79      | 0.76   | 0.77     | 10883   |
| Weighted avg | 0.80      | 0.81   | 0.80     | 10883   |

### Random Forest
|              | Precision | Recall | F1-score | Support |
|--------------|-----------|--------|----------|---------|
| Classe 0     | 0.88      | 0.81   | 0.85     | 3607    |
| Classe 1     | 0.91      | 0.95   | 0.93     | 7276    |
| Accuracy     |           |        | 0.90     | 10883   |
| Macro avg    | 0.90      | 0.88   | 0.89     | 10883   |
| Weighted avg | 0.90      | 0.90   | 0.90     | 10883   |

## Iterações de Otimização

### Primeira Iteração
- **Ajustes**: Tunagem dos hiperparâmetros da Árvore de Decisão e do Random Forest.
- **Resultados**: Melhoria nos scores de precisão e recall para ambas as classes.

### Segunda Iteração
- **Ajustes**: Implementação de técnicas de balanceamento de dados (SMOTE).
- **Resultados**: Aumento do F1-score e melhor equilíbrio entre precisão e recall.

## Métricas finais do Modelo Otimizado

### Random Forest Otimizado
|              | Precision | Recall | F1-score | Support |
|--------------|-----------|--------|----------|---------|
| Classe 0     | 0.90      | 0.85   | 0.87     | 3607    |
| Classe 1     | 0.93      | 0.97   | 0.95     | 7276    |
| Accuracy     |           |        | 0.92     | 10883   |
| Macro avg    | 0.91      | 0.91   | 0.91     | 10883   |
| Weighted avg | 0.92      | 0.92   | 0.92     | 10883   |

## Linhas de ações futuras

- **Otimização de hiperparâmetros**: Continuar ajustando os hiperparâmetros para melhorar o desempenho do modelo.
- **Balanceamento de dados**: Utilizar técnicas avançadas de balanceamento para lidar com classes desbalanceadas.
- **Integração com sistemas de reserva**: Implementar o modelo preditivo nos sistemas de reserva de hotéis para prever cancelamentos em tempo real.
- **Análise de novas variáveis**: Incluir novas variáveis que possam impactar a previsão de cancelamentos.

## Conclusões

Com base nos scores fornecidos, o modelo Random Forest apresentou um desempenho superior aos modelos Decision Tree e KNN para o problema específico em questão.

- O _F1-score_ do modelo Random Forest é mais alto do que o dos modelos Decision Tree e KNN para ambas as classes, sugerindo um melhor equilíbrio entre precisão e recall.
- Tanto os scores de _Recall_ quanto de _Precision_ do modelo Random Forest são mais altos do que os dos modelos Decision Tree e KNN para ambas as classes.
- A acurácia geral do modelo Random Forest é de 0.90, superior à do modelo Decision Tree (0.87) e do modelo K
