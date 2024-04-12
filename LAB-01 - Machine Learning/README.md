1. Acesse a página **ML Automatizado** no [Azure Machine Learning Studio](https://ml.azure.com/home?tid=da49a844-e2e3-40af-86a6-c3819d704f49)

2. Crie um novo trabalho de ML automatizado com as configurações:
#### Configurações básicas:

* **Nome do trabalho**: mslearn-bike-automl
* **Novo nome do experimento**: mslearn-bike-rental
* **Descrição**: Aprendizado de máquina automatizado para previsão de aluguel de bicicletas
* **Marcadores**: nenhum

#### Tipo de tarefa e dados:

* **Selecione o tipo de tarefa**: Regressão
* **Selecionar conjunto de dados**: crie um novo conjunto de dados com as configurações:

    * **Tipo de dados**:

        * **Nome**: alugueldebicicletas
        * **Descrição**: dados históricos de aluguel de bicicletas
        * **Tipo**: Tabular

     * **Fonte de dados**:

        * Selecione Dos **arquivos da web**.
    
     * **URL da Web**:

        * **URL da Web**: https://aka.ms/bike-rentals
        * **Ignorar validação de dados**: não selecionar
    
     * **Configurações**:

        * **Formato de arquivo**: Delimitado
        * **Delimitador**: Vírgula
        * **Codificação**: UTF-8s
        * **Cabeçalhos de coluna**: Apenas o primeiro arquivo possui cabeçalhos
        * **Pular linhas**: Nenhum
        * **O conjunto de dados contém dados multilinhas**: Não selecione

     * **Esquema**:

        * Incluir todas as colunas exceto **Caminho**
        * Revise os tipos detectados automaticamente
        
3. Selecione o conjunto de dados de **aluguel de bicicletas** depois de criá-lo.

#### Configurações de tarefa:

* **Tipo de tarefa**: Regressão
* **Conjunto de dados**: aluguel de bicicletas
* **Coluna de destino**: Aluguéis (inteiro)
* **Configurações adicionais**:

    * **Métrica primária**: NormalizedRootMeanSquaredError (raiz do erro quadrático médio normalizado)
    * **Explique o melhor modelo** : Não selecionado
    * **Usar todos os modelos suportados**: Não selecionado
    * **Modelos permitidos**: Selecione apenas **RandomForest** e **LightGBM**

* Expanda a seção **Limites**.

    * **Máximo de testes**: 3
    * **Máximo de testes simultâneos**: 3
    * **Máximo de nós**: 3
    * **Limite de pontuação da métrica**: 0.085
    * **Tempo limite**: 15
    * **Tempo limite de iteração**: 15
    * **Habilitar rescisão antecipada**: Selecionado

* **Validação e teste**:

    * **Tipo de validação**: divisão de validação de treinamento
    * **Porcentagem de dados de validação**: 10
    * **Conjunto de dados de teste**: Nenhum

#### Calcular

* **Selecione o tipo de computação**: sem servidor
* **Tipo de máquina virtual**: CPU
* **Camada de máquina virtual**: Dedicada
* **Tamanho da máquina virtual**: Standard_DS3_V2
* **Número de instâncias**: 1

4. Envie o trabalho de treinamento e aguarde ser concluído.


#### Avalie o melhor modelo

1. Na guia **Visão geral** do trabalho automatizado de aprendizado de máquina, observe o **melhor resumo do modelo**.

2. Selecione o texto em **Nome do algoritmo** do melhor modelo para visualizar seus detalhes.

3. Na guia **Métricas** você consegue verificar informações e gráficos que mostram o desempenho do modelo selecionado.

#### Modelo

1. Na guia **Modelos** selecione Criar → De uma saída do trabalho
2. Selecione o melhor modelo visto anteriormente e preencha as informações


#### Pontos de Extremidade
1. Na guia **Pontos de Extremidade** selecione Criar
2. Selecione o Modelo criado anteriormente
3. Implantar
4. Selecione o Ponto de Extremidade
5. Na aba **Testar**, insira os seguintes dados:

```
 {
   "Inputs": { 
     "data": [
       {
         "day": 1,
         "mnth": 1,   
         "year": 2022,
         "season": 2,
         "holiday": 0,
         "weekday": 1,
         "workingday": 1,
         "weathersit": 2, 
         "temp": 0.3, 
         "atemp": 0.3,
         "hum": 0.3,
         "windspeed": 0.3 
       }
     ]    
   },   
   "GlobalParameters": 1.0
 }
```

6. Clique no botão **Teste**

5. Revise os resultados do teste, semelhantes a estes:

~~~json
 {
  "Results": [
    356.9253888264152
  ]
}
~~~

   Pronto, você acabou de criar e treinar um modelo que prevê o número de aluguels de bicicletas esperados em um determinado dia, com base em características sazonais e meteorológicas.

   Caso tenha criado uma conta gratuita, após fazer os testes é recomendado excluir as sessões e recursos para não ocasionar em cobranças caso expire limite do uso grátis.
