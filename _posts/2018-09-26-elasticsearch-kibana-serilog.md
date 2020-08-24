---
layout: post
title: Logs com ElasticSearch, Kibana e Serilog
category: elasticsearch
date: 2018-09-26 18:35:13 -0300
background: ''
subtitle: ''
---
  
### ElasticSearch, Kibana, Serilog?  
  
Resumindo, o **ElasticSource** é uma base de dados open source utilizado para indexar logs e dados para análise. **Kibana** é uma interface visual para visualização do ElasticSource e o **Serilog** é um plugin para .net core para geração de logs.  
  

### Sim!, ElasticSearch!.  
  
Não vamos fugir, o ElasticSearch é cada vez mais popular é são vastos os exemplos e referências de uso na comunidade. Existem alguns motivos que aumentam essa aderência:  
  
* É grátis e open source  
* API Rest  
* Rápido! :)  
* Escalável  
* Fácil de configurar  
  
### Configuração  
    
* Crie o diretório.  
  
```javascript
mkdir artigo
cd artigo
```  
  
* Crie um novo projeto .Net Core
  
```javascript
dotnet new mvc -n artigo-elastic -o src
```  
  
* Abre o projeto no Visual Studio ou Visual Studio Code  
  
```javascript
cd artigo-elastic  
code.  
```  
  
* Cria um docker compose file (**docker-compose.yml**) com o Elasticserach e Kibana.  
**Para utilizar o docker em sua versão para windows não é necessário criar o docker-network**
  
```javascript
version: '3.1'

services:

  elasticsearch:
   image: docker.elastic.co/elasticsearch/elasticsearch:6.2.4
   container_name: elasticsearch
   ports:
    - "9200:9200"
   volumes:
    - elasticsearch-data:/usr/share/elasticsearch/data
   networks:
    - docker-network

  kibana:
   image: docker.elastic.co/kibana/kibana:6.2.4
   container_name: kibana
   ports:
    - "5601:5601"
   depends_on:
    - elasticsearch
   networks:
    - docker-network
  
networks:
  docker-network:
    driver: bridge

volumes:
  elasticsearch-data:  
```  
  
* Execute o docker  
  
```javascript
docker-compose up -d
```  
  
* Digite no browser o endereço: http://localhost:9200 para acessar o Elasticsearch.  
  
* Digite no browser o endereço: http://localhost:5601 para acessar o Kibana.
  
* Adicione os pacotes Nuget ao projeto  
  
  
```javascript
dotnet add package Serilog
dotnet add package Serilog.Sinks.ElasticSearch
dotnet add package Serilog.Extensions.Logging
dotnet restore
```  
  
* Realize as configurações no appsettings.json  
  
```javascript
{
  "Logging": {
    "LogLevel": {
        "Default": "Information",
        "System": "Information",
        "Microsoft": "Information"
    }
  },
  "ElasticConfiguration": {
    "Uri": "http://localhost:9200/"
  }
}
```  
  
* Configure o log no seu startup.cs  
  
```javascript
using Microsoft.Extensions.Logging;
using Serilog;
using Serilog.Sinks.Elasticsearch;
```  
...  
```javascript
public Startup(IConfiguration configuration, IHostingEnvironment hostingEnvironment)
{
    var builder = new ConfigurationBuilder()
        .SetBasePath(hostingEnvironment.ContentRootPath)
        .AddJsonFile("appsettings.json", optional: true, reloadOnChange: true)
        .AddJsonFile($"appsettings.{hostingEnvironment.EnvironmentName}.json", reloadOnChange: true, optional: true)
        .AddEnvironmentVariables();

    Configuration = builder.Build();

    var elasticUri = Configuration["ElasticConfiguration:Uri"];

    Log.Logger = new LoggerConfiguration()
        .Enrich.FromLogContext()
        .WriteTo.Elasticsearch(new ElasticsearchSinkOptions(new Uri(elasticUri))
        {
            AutoRegisterTemplate = true,
        })
    .CreateLogger();
}
```  
...  
```javascript
public void Configure(IApplicationBuilder app, IHostingEnvironment env, ILoggerFactory loggerFactory)
{
    /// ...
    
    loggerFactory.AddSerilog();
    
    /// ...
}
```  
  
* Execute sua aplicação MVC, **e vamos começar!!!** 
  
### Kibana index pattern  
  
Para iniciar a visualização dos dados é necessários criar um indíce, acesse **Management** e defina o nome (ex: log20180926)  
Em seguida selecione o campo **timestastamp** e clique em **Create index pattern**  
  
Nesse momento já é possível visualizar os logs acessando a opção **Discovery**  
 
 <div>
  <row>
     <img src="/img/posts/kibana0.jpg" style="display: block; margin: 0 auto; width: 90%"> 
  </row>
</div>
<br>

 <div>
  <row>
     <img src="/img/posts/kibana1.jpg" style="display: block; margin: 0 auto; width: 90%"> 
  </row>
</div>
<br>

 
Agora é com vocês, aprofunde seus estudos e divirta-se!  
