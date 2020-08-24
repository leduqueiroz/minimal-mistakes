---
layout: post
title: Recuperando valores do appsettings.json
category: dotnetcore
date: 2018-07-28 18:35:13 -0300
background: ''
subtitle: ''
---
  
Boa tarde!  
Nesse artigo vou explicar brevemente e exemplificar a maneira mais fácil de recuperar as configurações de sua aplicação.  
  
### appsettings.json  

A primeira coisa importante para sabermos é que o arquivo não necessariamente precisa ter esse nome e que você pode escolher o mesmo e
sua localização de acordo com sua necessidade, desde que informe o mesmo no *ConfigurationBuilder()*.  

No nosso exemplo o arquivo receberá o nome *appsettings.json* e terá a seguinte estrutura:  

> ![an image alt text]({{ site.baseurl }}/img/posts/appsettings/ex1.jpg "an image title")  
  
### Option Class  

O próximo passo é criar sua classe com a estrutura do seu arquivo, nesse exemplo iremos recuperar a chave *AppSettings* e suas propriedades,
nossa classe fica assim:  
  
> ![an image alt text]({{ site.baseurl }}/img/posts/appsettings/ex2.jpg "an image title")  
  
Na classe *Startup.cs* inclua no método *ConfigureServices()* para registrar sua configuração:  

> ![an image alt text]({{ site.baseurl }}/img/posts/appsettings/ex3.jpg "an image title")  
  
No seu *Controller* crie a propiedade que irá receber sua configuração e atribua um valor através do construtor e acesse os valores conforme sua necessidade.  
  
> ![an image alt text]({{ site.baseurl }}/img/posts/appsettings/ex4.jpg "an image title")  
  
### Importante  
  
Com o framework .NET Core o sistema de configuração é facilitado e mais flexível que o método antigo (framework .net), existem tambem outras possibilidades
de configuração que são detalhadas no site oficial da Microsoft: <https://docs.microsoft.com/en-us/aspnet/core/fundamentals/configuration>.  
  
**Bons estudos!**  
