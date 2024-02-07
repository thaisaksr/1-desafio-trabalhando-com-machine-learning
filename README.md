# 1 trabalhando-com-machine-learning -Azure

Passo a passo de experimento de Aprendizagem Automatizada, de Regressão, utilizando A Azure Machine Learning, realizado como desafio de projeto no Bootcamp Microsoft Azure AI Fundamentals da Dio.me

## Passo 1
* Criar uma conta no [https://azure.microsoft.com/pt-br/free]

## Passo 2
* Acessar a plataforma do Azure em portal.azure.com
* Buscar por "Azure Machine Learning" no campo de busca e selecionar o card referido.

## Passo 3
* Clicar em "Criar", para criar um novo workspace
![image](https://github.com/thaisaksr/1-desafio-trabalhando-com-machine-learning/assets/149262815/107935d0-b1ac-43bb-bda3-49863fcca536)

## Passo 4
* Criar um novo "resource group", criar um "nome", a "região", e clicar em "Examinar e criar"

* *Assinatura:* * sua assinatura do Azure .

* *Grupo de recursos:** : Crie ou selecione um grupo de recursos .

* *Nome:** Insira um nome exclusivo para seu espaço de trabalho .

* *Região:* * Selecione a região geográfica mais próxima .

* *Conta de armazenamento:** observe a nova conta de armazenamento padrão que será criada para seu espaço de trabalho .

* *Cofre de chaves:** Observe o novo cofre de chaves padrão que será criado para seu espaço de trabalho .

* *Insights de aplicativos:** observe o novo recurso padrão de insights de aplicativos que será criado para seu espaço de trabalho .

* *Registro de contêiner:** Nenhum ( um será criado automaticamente na primeira vez que você implantar um modelo em um contêiner ).


![image](https://github.com/thaisaksr/1-desafio-trabalhando-com-machine-learning/assets/149262815/9b2c71de-9535-4bff-a7bf-38d36605a278)

* *Examinar+ criar**

* Aguardar até que a validação seja aprovada, e então clicar em "criar"

  ## Passo 5

* A implantação fica em andamento e pode ser acompanhada na tela que é aberta automaticamente

  ![image](https://github.com/thaisaksr/1-desafio-trabalhando-com-machine-learning/assets/149262815/98f3fc03-61a8-4f31-aaff-48823fcff6a7)

* Esta é a tela de finalização. Agora podemos clicar em "ir para o recurso".

  ![image](https://github.com/thaisaksr/1-desafio-trabalhando-com-machine-learning/assets/149262815/2945698f-fc4b-43b1-9cd3-b352c64cdc1a)

* Na tela do recurso, clicar em "Iniciar estúdio"

  ![image](https://github.com/thaisaksr/1-desafio-trabalhando-com-machine-learning/assets/149262815/1eae82ed-ed9f-4ac8-b2a3-0235fdefde85)

  ## Passo 6

* O diretório do workspace é então aberto.
* Posso visualizar todos os workspaces existentes, clicando em "all workspaces", do lado esquerdo.

  ![image](https://github.com/thaisaksr/1-desafio-trabalhando-com-machine-learning/assets/149262815/ad48c0a1-45d9-425b-9ad3-c792bfec8cb2)

  ## Passo 7
* O workspace escolhido é aberto. Preciso agora entrar no ambiente "Automated ML" e clicar em criar um "new ML automated job"
![image](https://github.com/thaisaksr/1-desafio-trabalhando-com-machine-learning/assets/149262815/10a7168e-3498-43f5-9bc4-e56d5a51d38b)

## Passo 8
* Preencher os dados do job com as informações (fornecidas pela documentação da Microsoft)

* 7.1 -> Preenchimento das informações básicas

![image](https://github.com/thaisaksr/1-desafio-trabalhando-com-machine-learning/assets/149262815/2121ecd0-cd92-455c-98eb-9a6624be5c01)

* 7.2 -> Escolha do tipo de tarefa (Regressão) e criação do dataset
![image](https://github.com/thaisaksr/1-desafio-trabalhando-com-machine-learning/assets/149262815/e483e4dc-844f-455c-a848-de139d7af392)

* 7.3 -> Preenchimento das informações do dataset
![image](https://github.com/thaisaksr/1-desafio-trabalhando-com-machine-learning/assets/149262815/e68534c5-32f3-4cd9-a87e-e5818ce6040c)

* 7.4 -> Escolha da fonte dos dados
![image](https://github.com/thaisaksr/1-desafio-trabalhando-com-machine-learning/assets/149262815/6d57d72a-84c1-414c-b765-355265a98de0)

* 7.5 -> Inclusão da url do dataset. A url passa por uma verificação e validação.
![image](https://github.com/thaisaksr/1-desafio-trabalhando-com-machine-learning/assets/149262815/74c639fd-714e-49c3-89b6-7d3963948429)

* 7.6 -> Os dados devem estar com as seguintes configurações
![image](https://github.com/thaisaksr/1-desafio-trabalhando-com-machine-learning/assets/149262815/4d9885d6-2b0d-48d2-be5d-cd602a3f310f)

* 7.7 -> Ele traz uma visualização do schema. Não é necessário alterar nenhuma informação.
![image](https://github.com/thaisaksr/1-desafio-trabalhando-com-machine-learning/assets/149262815/ef328e46-197f-49c8-b0fb-6064411d7af4)

* 7.8 -> Por fim, ele traz todas informações para review, e clicamos em "criar", para criar o dataset.
![image](https://github.com/thaisaksr/1-desafio-trabalhando-com-machine-learning/assets/149262815/1c2eaf1a-7adc-4981-89b5-6c540856821e)

* 7.9 -> Para avançar, selecionamos o dataset, e clicamos em "next"
![image](https://github.com/thaisaksr/1-desafio-trabalhando-com-machine-learning/assets/149262815/a1c46348-7e53-4464-87bd-1c352253bb78)

*7.10 -> Configurações adicionais :

_Métrica primária_: raiz do erro quadrático médio normalizado
_Explique o melhor modelo_: Não selecionado
_Usar todos os modelos suportados_ : Desmarcado . Você restringirá o trabalho para tentar apenas alguns algoritmos específicos.
_Modelos permitidos_ : Selecione apenas RandomForest e LightGBM — normalmente você gostaria de tentar o máximo possível, mas cada modelo adicionado aumenta o tempo necessário para executar o trabalho.
  
_Limites_ : expanda esta seção

_Máximo de testes_ : 3

_Máximo de testes simultâneos_ : 3

_Máximo de nós_ : 3

_Limite de pontuação da métrica_ : 0,085 ( para que, se um modelo atingir uma pontuação da métrica de erro quadrático médio normalizado de 0,085 ou menos, o trabalho termina. )
  
_Tempo limite_: 15

_Tempo limite de iteração_ : 15

_Habilitar rescisão antecipada_ : selecionado

_Validação e teste_ :

_Tipo de validação_: divisão de validação de trem

_Porcentagem de dados de validação_ : 10

_Conjunto de dados de teste_ : Nenhum

7.11 -> Não é necessário setar nenhuma informação diferença da parte de Computação
![image](https://github.com/thaisaksr/1-desafio-trabalhando-com-machine-learning/assets/149262815/8775446f-313f-4d59-b7d6-6e0fdf342f91)


Calcular :

Selecione o tipo de computação : sem servidor

Tipo de máquina virtual : CPU

Camada de máquina virtual : Dedicada

Tamanho da máquina virtual : Standard_DS3_V2*
Número de instâncias : 1

7.12 -> 7.12 -> As informações são trazidas e podemos enviar o trabalho de treinamento


* Se a sua assinatura restringir os tamanhos de VM disponíveis para você, escolha qualquer tamanho disponível.

Envie o trabalho de treinamento. Ele inicia automaticamente.

Espere o trabalho terminar. Pode demorar um pouco – agora pode ser um bom momento para uma pausa para o café!

![image](https://github.com/thaisaksr/1-desafio-trabalhando-com-machine-learning/assets/149262815/28a962be-0760-4d6b-859e-b0822b637658)

## Passo 8

![image](https://github.com/thaisaksr/1-desafio-trabalhando-com-machine-learning/assets/149262815/7bd02f4f-5919-40a7-9ae0-f43a0c283d4b)

![image](https://github.com/thaisaksr/1-desafio-trabalhando-com-machine-learning/assets/149262815/106563f9-6e23-44db-abc3-c1af14ffde7f)

## Passo 9

*Avaliar Métrica
9.1 -> Acessar as informações do modelo conforme imagem abaixo

Quando o trabalho automatizado de aprendizado de máquina for concluído, você poderá revisar o melhor modelo treinado.

Na guia Visão geral do trabalho automatizado de aprendizado de máquina, observe o melhor resumo do modelo.

![image](https://github.com/thaisaksr/1-desafio-trabalhando-com-machine-learning/assets/149262815/2fde32a6-b418-47bb-bb68-d785534ccf99)

9.2 -> Acessar o job

![image](https://github.com/thaisaksr/1-desafio-trabalhando-com-machine-learning/assets/149262815/8908ead6-ca1e-498c-80ee-10be74e3060a)

9.3 -> Acessar as métricas

![image](https://github.com/thaisaksr/1-desafio-trabalhando-com-machine-learning/assets/149262815/a597b595-e5dc-49d7-9962-9ddcc15d8a09)

## Passo 10
*Deploy e Teste do Modelo

*10.1 -> De volta à página do modelo, escolhemos a opção de Deploy Web Service.

![image](https://github.com/thaisaksr/1-desafio-trabalhando-com-machine-learning/assets/149262815/14e226d8-fd62-4af7-8a1d-6255ae795051)

10.2 -> Preencher com as informações fornecidas na documentação e clicar em "Deploy"

![image](https://github.com/thaisaksr/1-desafio-trabalhando-com-machine-learning/assets/149262815/2a81cb49-f033-499d-b733-60391e074cb8)

10.3 -> Receberemos a notificação de que o deploy está completo e, no menu esquerdo, vamos clicar na aba Endpoints.
![image](https://github.com/thaisaksr/1-desafio-trabalhando-com-machine-learning/assets/149262815/886779ff-d5d2-4779-81b8-768c82f94595)

10.4 -> Na tela de Endpoint, confirmamos o status "Succeed" do deploy, e clicamos na aba "Test"
![image](https://github.com/thaisaksr/1-desafio-trabalhando-com-machine-learning/assets/149262815/3464ab4d-b0f8-4ad8-a0d2-22ded5a8d980)


10.4 -> Substituímos o json existente, pelo código fornecido pela documentação, e depois clicamos em "Test".
10.5 -> Resultado do Teste

Aguarde o início da implantação – isso pode levar alguns segundos. O status de implantação do endpoint de previsão de aluguel será indicado na parte principal da página como Running .

Aguarde até que o status da implantação mude para Succeeded . Isso pode levar de 5 a 10 minutos.

##Códigos:

###Input

``` {
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

###Output


Revise os resultados do teste, que incluem um número previsto de aluguéis com base nos recursos de entrada - semelhante a este:

```
{
  "Results": [
    312.6685563926644
  ]
}
```










