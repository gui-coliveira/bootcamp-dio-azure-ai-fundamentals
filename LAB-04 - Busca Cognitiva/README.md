# Utilizando AI Search para indexação e consulta de dados

## Criação de Recursos
1. Acesse o Microsoft Azure 
2. Crie um recurso de **Azure AI Search**
3. Crie um recurso de **Serviços Cognitivos**
4. Crie um recurso de **Contas de Armazenamento** selecionando: <br>
   • Desempenho **Standard** <br>
   • Redundância **LRS (armazenamento com redundância local)**
   
6. Nas configurações da conta de armazenamento, habilite a opção **Permitir acesso anônimo ao Blob**
<img src="https://github.com/gui-coliveira/bootcamp-dio-azure-ai-fundamentals/blob/main/LAB-04%20-%20Busca%20Cognitiva/Source/storage-settings.png">

## Configurações do Contêiner
1. Nas opções de armazenamento de dados, selecione 'Contêineres'

8. Crie um Contêiner. Em Nível de acesso anônimo, selecione **Contêiner (acesso de leitura anônimo para contêineres e Blobs)**

9. Selecione o Contêiner criado e Carregue os arquivos presentes na [Documentação disponibilizada aqui.](https://microsoftlearning.github.io/mslearn-ai-fundamentals/Instructions/Labs/11-ai-search.html)

## Importação e indexação dos dados no AI Search
1. No recurso **AI Search**, selecione a opção **Importar Dados**

11. Selecione a Fonte: **Armazenamento de Blob do Azure**, preencha as informações e selecione o Contêiner criado anteriormente

## Consulta e pesquisa de dados
1. Voltando ao AI Search, selecione a opção **Gerenciador de Pesquisa**

13. Vamos utilizar um comando para verificar se a indexação foi feita corretamente:
```
search=*&$count=true 
```
<img src="https://github.com/gui-coliveira/bootcamp-dio-azure-ai-fundamentals/blob/main/LAB-04%20-%20Busca%20Cognitiva/Source/output1.png">

14. Podemos verificar as ocorrências que foram feitas em Chicago, por exemplo
```
search=locations:'Chicago'
```
<img src="https://github.com/gui-coliveira/bootcamp-dio-azure-ai-fundamentals/blob/main/LAB-04%20-%20Busca%20Cognitiva/Source/output2.png">

15. E ocorrências com sentimento negativo, positivo ou neutro
```
search=sentiment:'negative'
```
