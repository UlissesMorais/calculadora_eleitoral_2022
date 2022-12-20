# Calculadora eleitoral para Deputado Federal

Modelo de Machine Learning que prevê a probabilidade de um candidato a deputado federal ser eleito, utilizando dos dados disponibilizados pelo Tribunal Superior Eleitoral (TSE) referente às eleições de 2022.


## Índice

* [Introdução](#Introdução)
* [Tecnologias](#Tecnologias)
* [Escopo e funcionalidades](#Escopo-e-funcionalidades)
    * [1° notebook](#notebook_1)
    * [2° notebook](#2°-notebook)
    * [3° notebook](#3°-notebook)
    * [4° notebook](#4°-notebook)
* [Workflow do projeto](#Workflow-do-projeto)
* [Próximos passos](#Próximos-passos)
* [Conclusão](#Conclusão)


## Introdução

Este projeto teve como objetivo criar um modelo de Machine Learning que seja capaz de prever a probabilidade de um candidato a Deputado Federal ser eleito, baseado nas informações que o Tribunal Superior Eleitoral disponibiliza em seu portal de **[Dados Abertos](https://dadosabertos.tse.jus.br/)**. O projeto é dividido em etapas típicas de um projeto de ML (download dos arquivos de dados, análise exploratória, tratamento dos mesmos etc.). Cada etapa é abordada em um *Jupyter notebook* específico, para facilitar o workflow do projeto.

Ao final, finalizada a escolha do melhor modelo e tunagem dos hiperparâmetros, foi realizado o deploy do modelo e criada uma interface para interação com o usuário utilizando o *Spaces* da Hugging Face. O **Web App** pode ser acessado por este
**[link](https://huggingface.co/spaces/UlissesMorais/depfed_previsao_eleicao)**.
 
 
## Tecnologias

* Python 3.10
* Xgboost 1.7.2
* Scikit-learn 1.0.2


## Escopo e funcionalidades

O projeto está dividido em 4 notebooks:

&nbsp;&nbsp;&nbsp;**1.**  insights_dados

&nbsp;&nbsp;&nbsp;**2.**  monta_dataset

&nbsp;&nbsp;&nbsp;**3.**  modelos_ml

&nbsp;&nbsp;&nbsp;**4.** avalia_previsoes


### notebook_1

Constitui uma análise exploratória dos dados, cujo objetivo é entender como diversos fatores influenciam e estão rtelacionados com o objetivo principal (ver se o candidato será ou não eleito). Portanto, montam-se diversos gráficos para entender melhor estas relações. Os *insights* gerados nesta parte são cruciais para a montagem do dataset que será fornecido aos modelos de *Machine Learning*.

### 2° notebook

Como próprio nome sugere, obtêm o dataset que posteriormente será dividido em treinamento e teste. Neste notebook é realizado o download dos arquivos de dados, análise exploratória, tratamento e montagem do dataset final. A descrição detalhada encontra-se no próprio notebook.


### 3° notebook

Neste notebook são montados vários modelos de ML, realizando seus treinamentos, otimização dos hiper parâmetrosede e avaliação usando *cross validation*. Para fins de aplicação e capacidade de generalização, foi utilizado o parâmetro de maior *F1_score* como o determinante na escolha modelo. Descrições detalhadas no notebook.


### 4° notebook

A partir das previsões do melhor modelo, neste notebook é realizada a análise de onde on modelo está errando e possíveis causas de erro. Nesta parte entra o conhecimento prévio sobre o que está sendo modelado. Por exemplo: Os dados originais não possuíam o número de seguidores em redes sociais dos candidatos, então alguns candidatos com milhões de seguidores e que foram eleitos não estavam com uma probabilidade alta pelo modelo. Logo, adquiridos os dados de redes sociais e implementados no modelo, melhoraram substancialmente as previsões.

## Workflow do projeto

Segue abaixo um diagrama com o workflow que foi realizado durante o desenvolvimento do modelo. Nota-se que a etapa iterativa do processo era a avaliação do modelo nos dados de teste e também a análise de erro das previsões, o que levou a levantar novas features como dados de redes sociais, quociente eleitoral etc.

![This is an image](/media/workflow_projeto_ft.PNG)


## Próximos passos

Durante a montagem do dataset não foram empregadas todas as *features* que poderiam ser exploradas na base de dados. Características como ocupação, origem de despasa da campanha, grau de instrução, estado civil, prefixos/sufixos no nome na urna etc. Também, pode-se trazer dados que não estejam nos dados do TSE como por exemplo foi feito com redes sociais.


## Conclusão

Os resultados obtidos são bem satisfatórios, empregando-se 24 features como inputs. Nos dados de teste o desempenho foi de 96.4% de acurácia, 63.2% de precisão, 70% de revocaçãoe e 66.35% de F1_score. Os dados mostram que o modelo foi capaz de encontrar padrões complexos nos dados, uma vez que prever resultados eleitorais é extremamente complexo. Montar este projeto foi uma ideia original, a fim de integrar áreas que gosto bastante como política, IA e matemática/estatística.

Sintam-se à vontade para alterar o modelo e tentar melhorá-lo. Para mais dúvidas e questionamentos, basta enviar um email para ulissesmorais27@gmail.com
