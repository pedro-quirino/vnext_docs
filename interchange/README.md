# Contestação as a Service

Este repositório agrupa todos os fontes necessários para executar a aplicação de constestação das bandeiras ELO, Visa e Mastercard.

# Introdução

A constestação é o processo em que uma autorização não é considerada como válida pelo portador. Dessa forma é realizada uma contestação de uma transação financeira para a instituição que autorizou essa transação.

# Passo a Passo

O processo de contestação é feito em duas etapas, sua primeira etapa é o recebimento das transações e nessa etapa quem fornece as transações é o resultado final do Clearing que tem como objetivo validar as transações em enviar através de mensageria para o Interchange. Desse modo para que uma transação possa ser contestada, deve primeiro ser conciliada pelo Clearing. 

Após esse processo, ocorre a segunda etapa que é a contestação propriamente dita, onde o Interchange fornece uma API de contestação que é realizada pelo usuário de modo que deve preencher os campos necessários para informar e garantir que essa transação realmente não foi de origem do portador.

Para cada bandeira (ELO, Visa e Mastercard) existem seus respectivos serviços, pois, cada uma possui suas peculiaridadaes no quesito de solicitação de informações do usuário.

**ELO**:
> A contestação é enviada através de Outgoing para a bandeira, ou seja, seus serviços de contestação não fornecem acompanhamento e muito menos retorno de dados.

**Mastercard**:
>A contestação é enviada através da API da propria mastercard, onde é construída uma abstração dessas orquestrações de serviços da mastercard através da API que construimos no interchange.

Visa:
>Em construção.

# Stack

* Spring
* Azure Service Bus
* PostgreSQL

# Arquitetura

![Image of Clearing Architecture](docs/AzureContestacao.png) 

# Legenda

1 Service Bus Queue [Queue]

```yaml
interchange:                               
    serviceBus:
        transactionListenerConnectionString: Endpoint=sb://VNEXTPATH/;SharedAccessKeyName=NossoSharedAccessKeyName;SharedAccessKey=NossoSharedAccessKey
        transactionListenerEntityQueue: queue
```

2 Service Bus Claim [Queue]

```yaml
interchange:
    serviceBus:
        claimSenderConnectionString: Endpoint=sb://VNEXTPATH/;SharedAccessKeyName=NossoSharedAccessKeyName;SharedAccessKey=NossoSharedAccessKey
        claimSenderEntityQueue: claim

```

3 Database Configuration

```yaml
interchange:                                  
    datasource:
        socketTimeout: 30000
        loginTimeout: 30000
        minimumIdle: 10
        maximumPoolSize: 50
        validationTimeout: 10000
        idleTimeout: 30000
        connectionTimeout: 30000
        autoCommit: false
        initializationFailFast: false
        executeLiquibase: true
        habilitaTipoTenant: true
        common:
            dataBaseType: postgresql
            dataSourceClassName: org.postgresql.ds.PGSimpleDataSource
            port: 5432
            connectionTestQuery: SELECT 1
            ssl: false
        pier:    
            dataBaseType: postgresql
            dataSourceClassName: org.postgresql.ds.PGSimpleDataSource
            port: 5432
            databaseName: ...
            serverName: localhost
            username: ...
            password: ...
            appName: Interchange

```

4 Rest Service Port

```yaml
server:
    port: 8080

```