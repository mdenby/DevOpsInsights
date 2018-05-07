---

copyright:
  years: 2016, 2018
lastupdated: "2018-3-28"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Integrando ao Jenkins Pipeline

Depois de incluir o {{site.data.keyword.DRA_full}} em uma cadeia de ferramentas aberta e definir as políticas que ele monitora, será possível integrá-lo a um projeto Jenkins Pipeline. Defina um pipeline na interface da web do Jenkins ou em um _Jenkinsfile_ que você armazena no repositório de controle de fonte. É possível visualizar e administrar projetos Jenkins Pipelines da interface da web de Jenkins. 

O plug-in do IBM Cloud DevOps para o Jenkins integra os projetos do Jenkins com cadeias de ferramentas. Uma _cadeia de ferramentas_ é um conjunto de integrações de ferramentas que suporta tarefas de desenvolvimento, de implementação e de operações. O
poder coletivo de uma cadeia de ferramentas é maior que a soma de suas integrações de ferramentas individuais. As cadeias de ferramentas abertas são parte do serviço {{site.data.keyword.contdelivery_full}}. Para saber mais sobre o serviço {{site.data.keyword.contdelivery_short}}, veja [sua documentação](https://console.ng.bluemix.net/docs/services/ContinuousDelivery/cd_about.html). 

Depois de instalar o plug-in do IBM Cloud DevOps, será possível configurar o seu projeto do Jenkins para publicar resultados de teste no {{site.data.keyword.DRA_short}}, avaliar automaticamente a qualidade da compilação em portas e controlar o seu risco de implementação. Também é possível enviar notificações de tarefa para outras ferramentas em sua cadeia de ferramentas, como Slack e PagerDuty. Para ajudá-lo a controlar as implementações, a cadeia de ferramentas poderá incluir mensagens de implementação nas confirmações do Git e seus problemas Git ou JIRA relacionados. Também será possível visualizar suas implementações na página Conexões da cadeia de ferramentas. 

O plug-in fornece ações e CLIs pós-compilação para suportar a integração. O {{site.data.keyword.DRA_short}} agrega e analisa os resultados de testes de unidade, testes funcionais, ferramentas de cobertura de código, varreduras de código de segurança estática e varreduras de código de segurança dinâmica para determinar se seu código atende às políticas predefinidas nas portas em seu processo de implementação. Se o seu código não atender nem exceder uma
política, a implementação será interrompida, impedindo que as mudanças de risco sejam liberadas. É possível usar o {{site.data.keyword.DRA_short}} como uma
rede de segurança para o seu ambiente de entrega contínua, uma forma de implementar e melhorar padrões de qualidade ao longo do tempo e uma ferramenta de visualização
de dados para ajudá-lo a entender o funcionamento do seu projeto.

Se você estiver familiarizado com Jenkins Pipeline, leia sobre. Caso contrário, [consulte a documentação do Jenkins Pipeline](https://jenkins.io/doc/book/pipeline/) antes de continuar.

## Pré-Requisitos
{: #jenkins_prerequisites}

Deve-se ter acesso a um servidor que esteja executando um projeto Jenkins Pipeline. 

## Criando uma cadeia de ferramentas
{: #jenkins_create}

Antes de ser possível integrar o {{site.data.keyword.DRA_short}} a um projeto Jenkins, deve-se criar uma cadeia de ferramentas. 

1. Para criar uma cadeia de ferramentas, acesse a [página Criar uma cadeia de ferramentas](https://console.ng.bluemix.net/devops/create) e siga as instruções nessa página. 

2. Depois de criar a cadeia de ferramentas, inclua o {{site.data.keyword.DRA_short}} nela. Para obter instruções, veja a [documentação do {{site.data.keyword.DRA_short}}](https://console.ng.bluemix.net/docs/services/DevOpsInsights/index.html). 

## Instalando o plug-in
{: #jenkins_install}

Instale o plug-in em seu servidor Jenkins abrindo a interface do servidor e seguindo estas etapas:

1. Clique em **Gerenciar Jenkins**.
2. Clique em **Gerenciar plug-ins**. 
3. Clique na guia **Disponível**
4. Filtre para o `IBM Cloud DevOps`. 
5. Selecione **IBM Cloud DevOps**.
6. Clique em **Fazer download agora e instalar após a reinicialização**. 

O plug-in está disponível após a reinicialização do servidor.  

## Criando um pipeline
{: #jenkinsfile_create}

Os pipelines são definidos no menu de configuração do projeto Jenkins ou em um Jenkinsfile em seu repositório. Para continuar, crie ou abra um script ou Jenkinsfile para usar com o {{site.data.keyword.DRA_short}}. É possível seguir os formatos [declarativo](https://jenkins.io/doc/book/pipeline/syntax/#declarative-pipeline) ou de [script](https://jenkins.io/doc/book/pipeline/syntax/#scripted-pipeline).

## Expondo variáveis de ambiente necessárias

Abra a definição de pipeline. 

Na definição, inclua as variáveis de ambiente a seguir. Essas variáveis são necessárias para que o pipeline se integre ao {{site.data.keyword.DRA_short}}.

| Variável de Ambiente        | Definição    |
| ----------------------------|---------------|
| `IBM_CLOUD_DEVOPS_CREDS`    | As credenciais do {{site.data.keyword.Bluemix_notm}} Platform que você define no Jenkins usando o comando `credentials`. Por exemplo, `IBM_CLOUD_DEVOPS_CREDS = credentials('BM_CRED')`. Configurar a variável com esse comando configura duas ou mais variáveis de ambiente automaticamente: `IBM_CLOUD_DEVOPS_CREDS_USR` e `IBM_CLOUD_DEVOPS_CREDS_PSW` para o nome do usuário e a senha.  |
| `IBM_CLOUD_DEVOPS_ORG`      | A organização do {{site.data.keyword.Bluemix}} Platform à qual a cadeia de ferramentas pertence.     |
| `IBM_CLOUD_DEVOPS_APP_NAME` | O nome do aplicativo que sua cadeia de ferramentas implementa.   |
| `IBM_CLOUD_DEVOPS_TOOCLHAIN_ID` | O ID de sua cadeia de ferramentas. Abra a Visão geral da cadeia de ferramentas e veja a URL para determinar o ID. O formato da URL da cadeia de ferramentas é `https://console.ng.bluemix.net/devops/toolchains/[YOUR_TOOLCHAIN_ID]`.   |
| `IBM_CLOUD_DEVOPS_WEBHOOKURL` | O webhook que foi fornecido a você quando incluiu Jenkins em sua cadeia de ferramentas.   |

Para obter mais informações sobre o comando `credenciais`, consulte a [Documentação de pipeline do Jenkins](https://jenkins.io/doc/pipeline/tour/environment/#credentials-in-the-environment). 
{: tip}

Se você estiver usando o formato de pipeline com script, configure suas credenciais com `withCredentials` e seu ambiente com
`withEnv` em vez de `credentials` e `environment`, que são usados no exemplo a seguir. Para obter mais informações sobre `withCredentials`, consulte
[a documentação do Jenkins](https://jenkins.io/doc/pipeline/steps/credentials-binding/).
{: tip} 

Estas variáveis de ambiente e credenciais são usadas pelo plug-in do IBM Cloud DevOps para interagir com o DevOps Insights. Nesse exemplo, eles são configurados no formato de pipeline declarativo. 

```
environment {
        IBM_CLOUD_DEVOPS_CREDS = credentials('BM_CRED')
        IBM_CLOUD_DEVOPS_ORG = 'dlatest'
        IBM_CLOUD_DEVOPS_APP_NAME = 'Weather-App'
        IBM_CLOUD_DEVOPS_TOOLCHAIN_ID = '1111111-aaaa-2222-bbbb-333333333'
        IBM_CLOUD_DEVOPS_WEBHOOK_URL = 'https://jenkins:5a55555a-a555-5555-5555-a555aa55a555:55555555-5555-5555-5555-555555555555@devops-api.ng.bluemix.net/v1/toolint/messaging/webhook/publish'
    }
```


## Incluindo etapas do Cloud DevOps
O plug-in do DevOps Cloud inclui quatro etapas para pipelines do Jenkins para você usar. Use estas etapas nos pipelines para interagir com o DevOps Insights. 

* `publishBuildRecord`, que publica informações de construção no DevOps Insights
* `publishTestResult`, que publica resultados de teste no DevOps Insights
* `publishDeployRecord`, que publica registros de implementação no DevOps Insights
* `evaluateGate`, que utiliza políticas do DevOps Insights 

Inclua essas etapas em sua definição de pipeline onde quer que sua execução seja necessária. Por exemplo, é possível fazer upload dos resultados de teste após executar um teste e, em seguida, avaliar esses resultados em uma porta após eles serem transferidos por upload. 

### Publicando registros de construção

Publique os registros de construção com a etapa `publishBuildRecord`. Essa etapa requer quatro parâmetros.

| Parâmetro        | Definição    |
| ----------------------------|---------------|
| `gitBranch`    | O nome da ramificação Git usado pela construção.  |
| `gitCommit`      | O ID de confirmação Git usado pela construção.    |
| `gitRepo` | A URL do repositório Git.   |
| `result` | O resultado do estágio de construção. O valor é `SUCCESS` ou `FAIL`.   |

Este exemplo mostra esses parâmetros em um comando:

```
publishBuildRecord gitBranch: "${GIT_MASTER}", gitCommit: "${GIT_COMMIT}", gitRepo: "https://github.com/username/reponame", result:"SUCCESS"
```

O Jenkins Pipeline não mostra informações do Git como variáveis de ambiente. É possível obter o ID de confirmação Git usando o comando `sh(returnStdout: true, script: 'git rev-parse HEAD').trim()`.
{: tip}

### Publicando resultados de teste
Publique registros de construção com a etapa `publishTestResult`. Essa etapa requer dois parâmetros.

| Parâmetro        | Definição    |
| ----------------------------|---------------|
| `type`    | O tipo de resultado de teste. O valor disso deve ser `unittest` para testes de unidade, `fvt` para testes de verificação funcional ou `code` para testes de cobertura de código.  |
| `fileLocation`      | O local do arquivo de resultado de teste.    |

O exemplo a seguir mostra esses parâmetros em comandos. O primeiro comando publica resultados de teste de unidade do Mocha. O segundo comando publica os resultados do teste de cobertura de código. 

```
publishTestResult type:'unittest', fileLocation: './mochatest.json'
publishTestResult type:'code', fileLocation: './tests/coverage/reports/coverage-summary.json'
```

### Publicando registros de implementação

Publique registros de implementação com a etapa `publishDeployRecord`. Essa etapa requer dois parâmetros. Ela também pode aceitar um parâmetro opcional. 

| Parâmetro        | Definição    |
| ----------------------------|---------------|
| `environment`    | O ambiente no qual você implementa seu app. Para que o DevOps Insights funcione adequadamente, deve-se identificar um ambiente como `STAGING` e outro ambiente como `PRODUCTION`. |
| `result`      | O resultado do estágio de construção. O valor deve ser `SUCCESS` ou `FAIL`.    |
| `appUrl`      | _Opcional_: a URL usada para acessar seu aplicativo.    |

O exemplo a seguir mostra esses parâmetros em comandos. O primeiro comando publica o registro de implementação para um ambiente temporário. O segundo comando publica o registro de implementação para um ambiente de produção.

```
publishDeployRecord environment: "STAGING", appUrl: "http://staging-Weather-App.mybluemix.net", result:"SUCCESS"
publishDeployRecord environment: "PRODUCTION", appUrl: "http://Weather-App.mybluemix.net", result:"SUCCESS"
```

### Incluindo portas

Inclua portas em seu pipeline usando o comando `evaluateGate`. As portas utilizam as políticas do DevOps Insights, que configuram requisitos de teste para promoção de construção. 

Essa etapa requer um parâmetro. Ela também pode aceitar um parâmetro opcional. 

| Parâmetro        | Definição    |
| ----------------------------|---------------|
| `policy`    | O nome da política que a porta implementa. O nome da política é definido no DevOps Insights. |
| `forceDecision`      | _Opcional_: se o pipeline parará dependendo da decisão da porta. Configure esse parâmetro como `true` para parar a execução do pipeline se a porta falhar. Configure-a como `false` para permitir que o pipeline continue após uma falha da porta. Por padrão, o valor é `false`.     |

O exemplo a seguir mostra esses parâmetros em um comando. Nesse comando, o pipeline continua executando, independentemente da decisão da porta. 

```
evaluateGate policy: 'Weather App Policy', forceDecision: 'true'
```

### Comunicando-se com cadeias de ferramentas

Enviar status do pipeline para cadeias de ferramentas do {{site.data.keyword.Bluemix_notm}} usando o comando `notifyOTC`. Para saber mais sobre como integrar o Jenkins a cadeias de ferramentas, [veja a documentação](https://console.ng.bluemix.net/docs/services/ContinuousDelivery/toolchains_integrations.html#jenkins). É possível desconsiderar as etapas 6d a 6f, pois se aplicam apenas aos projetos Jenkins de formato livre.

Essa etapa requer dois parâmetros e também pode usar um opcional. 

| Parâmetro        | Definição    |
| ----------------------------|---------------|
| `stageName`    | O nome do estágio do pipeline atual. |
| `status`    | O status do estágio do pipeline atual. Usar `SUCCESS`, `FAILURE` ou `ABORTED` acionará automaticamente o destaque de cores no Slack.  |
| `webhookUrl`      | _Opcional_: a URL do webhook que é mostrada no quadro Jenkins de sua cadeia de ferramentas. Se você incluir esse parâmetro, seu valor substituirá aquele da variável de ambiente `IBM_CLOUD_DEVOPS_WEBHOOKURL`.   |

Os exemplos a seguir ilustram como usar a etapa `notifyOTC` em definições de pipeline declarativas e com script.

#### Pipeline declarativa
```
stage('Deploy') {
    steps {
      ...
    }

    post {
        success {
            notifyOTC stageName: "Deploy", status: "SUCCESS"
        }
        failure {
            notifyOTC stageName: "Deploy", status: "FAILURE", webhookUrl: "https://different-webhook-url@devops-api.ng.bluemix.net/v1/toolint/messaging/webhook/publish"
        }
    }
}
```

#### Pipeline com script
```
stage('Deploy') {
  try {
      ... (deploy steps)

      notifyOTC stageName: "Deploy", status: "SUCCESS"
  }
  catch (Exception e) {
      notifyOTC stageName: "Deploy", status: "FAILURE", webhookUrl: "https://different-webhook-url@devops-api.ng.bluemix.net/v1/toolint/messaging/webhook/publish"
  }
}
```

Em ambos os exemplos, a URL do webhook da cadeia de ferramentas é substituída somente em caso de falha. 

## Assegurando a rastreabilidade nas integrações da cadeia de ferramentas

Configure o seu ambiente do Jenkins para integrar com a sua cadeia de ferramentas do {{site.data.keyword.Bluemix_notm}} seguindo as instruções em [os {{site.data.keyword.Bluemix}} Docs](https://console.ng.bluemix.net/docs/services/ContinuousDelivery/toolchains_integrations.html#jenkins). É possível desconsiderar as etapas 6d a 6f, pois elas se aplicam somente aos projetos Jenkins de formato livre.

Integrar com uma cadeia de ferramentas lhe dá a rastreabilidade de ponta a ponta e o mapeamento de implementação. Depois de seguir as instruções de integração, inclua o comando `cf icd --create-connection $IBM_CLOUD_DEVOPS_WEBHOOK_URL $CF_APP_NAME` após as etapas de implementação. Esse comando conecta a sua integração do Jenkins a um app que está em execução no {{site.data.keyword.Bluemix_notm}} Platform. 

Este exemplo mostra uma etapa integral da implementação. O último comando é `cf icd --create-connection`. 

<pre>
sh '''
    echo "CF Login..."
    cf api https://api.ng.bluemix.net
    cf login -u $IBM_CLOUD_DEVOPS_CREDS_USR -p $IBM_CLOUD_DEVOPS_CREDS_PSW -o $IBM_CLOUD_DEVOPS_ORG -s staging
    echo "Deploying...."
    export CF_APP_NAME="staging-$IBM_CLOUD_DEVOPS_APP_NAME"
    cf delete $CF_APP_NAME -f
    cf push $CF_APP_NAME -n $CF_APP_NAME -m 64M -i 1
    <b>cf icd --create-connection $IBM_CLOUD_DEVOPS_WEBHOOK_URL $CF_APP_NAME</b>
'''
</pre>

Conforme descrito na documentação de integração do Jenkins, os plug-ins da CLI do CloudFoundry e do ICD do CloudFoundry devem ser instalados em seu servidor Jenkins. Também é necessário efetuar login no {{site.data.keyword.Bluemix}} Platform por meio do servidor para se conectar com ele.

## Exemplo de um pipeline declarativo

Este exemplo mostra um pipeline completo que é definido como um Jenkinsfile declarativo. 

```
#!groovy
/*
    This is an sample Jenkins file for the Weather App, which is a node.js application that has unit test, code coverage
    and functional verification tests, deploy to staging and production environment and use IBM Cloud DevOps gate.
    We use this as an example to use our plugin in the Jenkinsfile
    Basically, you need to specify required 4 environment variables and then you will be able to use the 4 different methods
    for the build/test/deploy stage and the gate
 */
pipeline {
    agent any
    environment {
        // You need to specify 4 required environment variables first, they are going to be used for the following IBM Cloud DevOps steps
        IBM_CLOUD_DEVOPS_CREDS = credentials('BM_CRED')
        IBM_CLOUD_DEVOPS_ORG = 'dlatest'
        IBM_CLOUD_DEVOPS_APP_NAME = 'Weather-V1'
        IBM_CLOUD_DEVOPS_TOOLCHAIN_ID = '1320cec1-daaa-4b63-bf06-7001364865d2'
        IBM_CLOUD_DEVOPS_WEBHOOK_URL = 'WEBHOOK_URL_PLACEHOLDER'
    }
    tools {
        nodejs 'recent'
    }
    stages {
        stage('Build') {
            environment {
                // get git commit from Jenkins
                GIT_COMMIT = sh(returnStdout: true, script: 'git rev-parse HEAD').trim()
                GIT_BRANCH = 'master'
                GIT_REPO = 'GIT_REPO_URL_PLACEHOLDER'
            }
            steps {
                checkout scm
                sh 'npm --version'
                sh 'npm install'
                sh 'grunt dev-setup --no-color'
            }
            // post build section to use "publishBuildRecord" method to publish build record
            post {
                success {
                    publishBuildRecord gitBranch: "${GIT_BRANCH}", gitCommit: "${GIT_COMMIT}", gitRepo: "${GIT_REPO}", result:"SUCCESS"
                }
                failure {
                    publishBuildRecord gitBranch: "${GIT_BRANCH}", gitCommit: "${GIT_COMMIT}", gitRepo: "${GIT_REPO}", result:"FAIL"
                }
            }
        }
        stage('Unit Test and Code Coverage') {
            steps {
                sh 'grunt dev-test-cov --no-color -f'
            }
            // post build section to use "publishTestResult" method to publish test result
            post {
                always {
                    publishTestResult type:'unittest', fileLocation: './mochatest.json'
                    publishTestResult type:'code', fileLocation: './tests/coverage/reports/coverage-summary.json'
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                // Push the Weather App to the {{site.data.keyword.Bluemix_notm}} Platform, staging space
                sh '''
                        echo "CF Login..."
                        cf api https://api.ng.bluemix.net
                        cf login -u $IBM_CLOUD_DEVOPS_CREDS_USR -p $IBM_CLOUD_DEVOPS_CREDS_PSW -o $IBM_CLOUD_DEVOPS_ORG -s staging

                        echo "Deploying...."
                        export CF_APP_NAME="staging-$IBM_CLOUD_DEVOPS_APP_NAME"
                        cf delete $CF_APP_NAME -f
                        cf push $CF_APP_NAME -n $CF_APP_NAME -m 64M -i 1

                        # use "cf icd --create-connection" to enable traceability
                        cf icd --create-connection $IBM_CLOUD_DEVOPS_WEBHOOK_URL $CF_APP_NAME

                        export APP_URL=http://$(cf app $CF_APP_NAME | grep urls: | awk '{print $2}')
                    '''
            }
            // post build section to use "publishDeployRecord" method to publish deploy record and notify OTC of stage status
            post {
                success {
                    publishDeployRecord environment: "STAGING", appUrl: "http://staging-${IBM_CLOUD_DEVOPS_APP_NAME}.mybluemix.net", result:"SUCCESS"
                    // use "notifyOTC" method to notify otc of stage status
                    notifyOTC stageName: "Deploy to Staging", status: "SUCCESS"
                }
                failure {
                    publishDeployRecord environment: "STAGING", appUrl: "http://staging-${IBM_CLOUD_DEVOPS_APP_NAME}.mybluemix.net", result:"FAIL"
                    // use "notifyOTC" method to notify otc of stage status
                    notifyOTC stageName: "Deploy to Staging", status: "FAILURE"
                }
            }
        }
        stage('FVT') {
            //set the APP_URL as the environment variable for the fvt
            environment {
                APP_URL = "http://staging-${IBM_CLOUD_DEVOPS_APP_NAME}.mybluemix.net"
            }
            steps {
                sh 'grunt fvt-test --no-color -f'
            }
            // post build section to use "publishTestResult" method to publish test result
            post {
                always {
                    publishTestResult type:'fvt', fileLocation: './mochafvt.json', environment: 'STAGING'
                }
            }
        }
        stage('Gate') {
            steps {
                // use "evaluateGate" method to leverage IBM Cloud DevOps gate
                evaluateGate policy: 'Weather App Policy', forceDecision: 'true'
            }
        }
        stage('Deploy to Prod') {
            steps {
                // Push the Weather App to the {{site.data.keyword.Bluemix_notm}} platform, production space
                sh '''
                        echo "CF Login..."
                        cf api https://api.ng.bluemix.net
                        cf login -u $IBM_CLOUD_DEVOPS_CREDS_USR -p $IBM_CLOUD_DEVOPS_CREDS_PSW -o $IBM_CLOUD_DEVOPS_ORG -s production

                        echo "Deploying...."
                        export CF_APP_NAME="prod-$IBM_CLOUD_DEVOPS_APP_NAME"
                        cf delete $CF_APP_NAME -f
                        cf push $CF_APP_NAME -n $CF_APP_NAME -m 64M -i 1

                        # use "cf icd --create-connection" to enable traceability
                        cf icd --create-connection $IBM_CLOUD_DEVOPS_WEBHOOK_URL $CF_APP_NAME
                        
                        export APP_URL=http://$(cf app $CF_APP_NAME | grep urls: | awk '{print $2}')
                    '''
            }
            // post build section to use "publishDeployRecord" method to publish deploy record and notify OTC of stage status
            post {
                success {
                    publishDeployRecord environment: "PRODUCTION", appUrl: "http://prod-${IBM_CLOUD_DEVOPS_APP_NAME}.mybluemix.net", result:"SUCCESS"
                    // use "notifyOTC" method to notify otc of stage status
                    notifyOTC stageName: "Deploy to Prod", status: "SUCCESS"
                }
                failure {
                    publishDeployRecord environment: "PRODUCTION", appUrl: "http://prod-${IBM_CLOUD_DEVOPS_APP_NAME}.mybluemix.net", result:"FAIL"
                    // use "notifyOTC" method to notify otc of stage status
                    notifyOTC stageName: "Deploy to Prod", status: "FAILURE"
                }
            }
        }
    }
}
``` 
