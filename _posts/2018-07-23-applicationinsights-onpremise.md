---
layout: post
title: API's On-Premise com Application Insights
category: Azure
date: 2018-07-23 18:35:13 -0300
background: ''
subtitle: ''
---

É normal que sua API hospedada no Microsoft Azure utilize os benefícios do Azure [Application Insights](https://azure.microsoft.com/en-us/pricing/details/application-insights/?irgwc=1&OCID=AID681541_aff_7593_1243925&tduid=(ir_T3QQgvSg3yuJ0uwxsWR-g2mvUkjVKcV7UShMwQ0)(7593)(1243925)(TnL5HPStwNw-HlHP2UwY7UMrCKBwYEupEw)()&irclickid=T3QQgvSg3yuJ0uwxsWR-g2mvUkjVKcV7UShMwQ0
), porem é possível que sua aplicação On-Premise 
também utilize essa funcionalidade.  

Nesse artigo irei pontuar alguns pontos importantes da configuração do ambiente e também exibir algumas análises disponíveis para visualização no Portal Azure.  

### Instalação  

A maneira mais simpples é instalar o **Application Insights Status Monitor** no seu servidor IIS, 
o download da aplicação pode ser realizado [AQUI](http://wordpress.redirectingat.com/?id=725X1342&site=unhandled.wordpress.com&xs=1&isjs=1&url=http%3A%2F%2Fgo.microsoft.com%2Ffwlink%2F%3FLinkId%3D506648&xguid=21949ab568485ffd7d916bc78a75e173&xuuid=c94fe1ddd6f0b9a518b9367c263d7dd2&xsessid=752a0001685a0b2de8a9959be6343695&xcreo=0&xed=0&sref=https%3A%2F%2Funhandled.wordpress.com%2F2018%2F02%2F01%2Fusing-azure-application-insights-with-on-premises-servers%2F&xtz=180&jv=13.6.5&bv=2.5.1
).  

> ![an image alt text]({{ site.baseurl }}/img/posts/aiazure1.jpg "an image title")  

### Configuração  

Depois de instalado o monitor irá exiti as aplicações publicadas em seu servidor:  

_OBS: Caso necessário defina o acesso para o grupo "Performance Monitor Users"._  

> ![an image alt text]({{ site.baseurl }}/img/posts/aisecutity.jpg "an image title")  

Após selecionar sua aplicação acesse sua conta da Microsoft Azure e configura um novo **resouce** ou selecione um existente.  

> ![an image alt text]({{ site.baseurl }}/img/posts/ailogin.jpg "an image title")  
> ![an image alt text]({{ site.baseurl }}/img/posts/airesource.jpg "an image title")  

Finalizado a configuração o agente iniciará o envio dos dados para a instância de Azure Application Insights.

#### Visualização  

> ![an image alt text]({{ site.baseurl }}/img/posts/aigraph1.jpg "an image title")  
> ![an image alt text]({{ site.baseurl }}/img/posts/aigraph2.jpg "an image title")  



