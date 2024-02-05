# 1-desafio-trabalhando-com-machine-learning
modelo de previsão com seus devidos pontos de extremidade configurados

## 1-Crie um espaço de trabalho do Azure Machine Learning

1- Entre no portal do Azure usando https://portal.azure.comsuas credenciais da Microsoft.

2- Selecione + Criar um recurso , pesquise Machine Learning e crie um novo recurso do Azure Machine Learning com as seguintes configurações:

**Assinatura:** sua assinatura do Azure .

**Grupo de recursos:** : Crie ou selecione um grupo de recursos .

**Nome:** Insira um nome exclusivo para seu espaço de trabalho .

**Região:** Selecione a região geográfica mais próxima .

**Conta de armazenamento:** observe a nova conta de armazenamento padrão que será criada para seu espaço de trabalho .

**Cofre de chaves:** Observe o novo cofre de chaves padrão que será criado para seu espaço de trabalho .

**Insights de aplicativos:** observe o novo recurso padrão de insights de aplicativos que será criado para seu espaço de trabalho .

**Registro de contêiner:** Nenhum ( um será criado automaticamente na primeira vez que você implantar um modelo em um contêiner ).

2-Selecione Revisar + criar e selecione Criar . Aguarde a criação do seu espaço de trabalho (pode demorar alguns minutos) e, em seguida, vá para o recurso implantado.

3-Selecione Launch Studio (ou abra uma nova guia do navegador e navegue até https://ml.azure.com e entre no Azure Machine Learning Studio usando sua conta da Microsoft). Feche todas as mensagens exibidas.

4-No estúdio Azure Machine Learning, você deverá ver seu espaço de trabalho recém-criado. Caso contrário, selecione Todos os espaços de trabalho no menu à esquerda e selecione o espaço de trabalho que você acabou de criar.

## Use aprendizado de máquina automatizado para treinar um modelo

No Azure Machine Learning Studio , veja a página Automated ML (em Authoring ).

Crie um novo trabalho de ML automatizado com as seguintes configurações, usando Next conforme necessário para avançar pela interface do usuário:

Configurações básicas :

Nome do trabalho : mslearn-bike-automl

Novo nome do experimento : mslearn-bike-rental

Descrição : Aprendizado de máquina automatizado para 

previsão de aluguel de bicicletas

Marcadores : nenhum

Tipo de tarefa e dados :


Selecione o tipo de tarefa : Regressão

Selecionar conjunto de dados : crie um novo conjunto de dados com as seguintes configurações:

Tipo de dados :

Nome : aluguel de bicicletas

Descrição : dados históricos de aluguel de bicicletas

Tipo : Tabular


Fonte de dados :

Selecione Dos arquivos da web

URL da Web :

URL da Web :https://aka.ms/bike-rentals

Ignorar validação de dados : não selecionar

Configurações :

Formato de arquivo : Delimitado

Delimitador : Vírgula

Codificação : UTF-8

Cabeçalhos de coluna : apenas o primeiro arquivo 
possui cabeçalhos

Pular linhas : Nenhum

O conjunto de dados contém dados multilinhas : não selecione

Esquema :

Incluir todas as colunas exceto Caminho

Revise os tipos detectados automaticamente
Selecione Criar . Após a criação do conjunto de dados, selecione o conjunto de dados de aluguel de bicicletas para continuar a enviar o trabalho de ML automatizado.

Configurações de tarefa :

Tipo de tarefa : Regressão

Conjunto de dados : aluguel de bicicletas

Coluna de destino : Aluguéis (inteiro)

Configurações adicionais :

Métrica primária : raiz do erro quadrático médio normalizado

Explique o melhor modelo : Não selecionado

Usar todos os modelos suportados : Desmarcado . Você restringirá o trabalho para tentar apenas alguns algoritmos específicos.

Modelos permitidos : Selecione apenas RandomForest e LightGBM — normalmente você gostaria de tentar o máximo possível, mas cada modelo adicionado aumenta o tempo necessário para executar o trabalho.

Limites : expanda esta seção

Máximo de testes : 3

Máximo de testes simultâneos : 3

Máximo de nós : 3

Limite de pontuação da métrica : 0,085 ( para que, se um modelo atingir uma pontuação da métrica de erro quadrático médio normalizado de 0,085 ou menos, o trabalho termina. )

Tempo limite : 15

Tempo limite de iteração : 15

Habilitar rescisão antecipada : selecionado

Validação e teste :

Tipo de validação : divisão de validação de trem

Porcentagem de dados de validação : 10

Conjunto de dados de teste : Nenhum

Calcular :

Selecione o tipo de computação : sem servidor

Tipo de máquina virtual : CPU

Camada de máquina virtual : Dedicada

Tamanho da máquina virtual : Standard_DS3_V2*
Número de instâncias : 1

* Se a sua assinatura restringir os tamanhos de VM disponíveis para você, escolha qualquer tamanho disponível.

Envie o trabalho de treinamento. Ele inicia automaticamente.

Espere o trabalho terminar. Pode demorar um pouco – agora pode ser um bom momento para uma pausa para o café!

## Avalie o melhor modelo

Quando o trabalho automatizado de aprendizado de máquina for concluído, você poderá revisar o melhor modelo treinado.

Na guia Visão geral do trabalho automatizado de aprendizado de máquina, observe o melhor resumo do modelo.

2- Selecione o texto em Nome do algoritmo do melhor modelo para visualizar seus detalhes.

3- Selecione a guia Métricas e selecione os gráficos residuais e predito_true se eles ainda não estiverem selecionados.

Revise os gráficos que mostram o desempenho do modelo. O gráfico de resíduos mostra **os resíduos** (as diferenças entre os valores previstos e reais) como um histograma. O gráfico **predito_true** compara os valores previstos com os valores verdadeiros.  

##Implantar e testar o modelo

Na guia Modelo do melhor modelo treinado pelo seu trabalho automatizado de machine learning, selecione Implantar e use a opção de serviço Web para implantar o modelo com as seguintes configurações:

Nome : prever-aluguéis

Descrição : Prever aluguel de bicicletas

Tipo de computação : Instância de Contêiner do Azure

Habilitar autenticação : selecionado

Aguarde o início da implantação – isso pode levar alguns segundos. O status de implantação do endpoint de previsão de aluguel será indicado na parte principal da página como Running .

Aguarde até que o status da implantação mude para Succeeded . Isso pode levar de 5 a 10 minutos.

## Testar o serviço implantado

Agora você pode testar seu serviço implantado.

No estúdio Azure Machine Learning, no menu esquerdo, selecione Endpoints e abra o ponto final em tempo real de previsão de alugueres .

Na página do endpoint em tempo real de previsão de aluguel, visualize a guia Teste .

No painel Dados de entrada para testar o endpoint , substitua o modelo JSON pelos seguintes dados de entrada:

Código
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


 Clique no botão Testar .

Revise os resultados do teste, que incluem um número previsto de aluguéis com base nos recursos de entrada - semelhante a este:


{
  "Results": [
    312.6685563926644
  ]
}
