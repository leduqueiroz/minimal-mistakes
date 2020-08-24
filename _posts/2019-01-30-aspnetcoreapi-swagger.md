---
layout: post
title: ASPNET.Core e Swagger
categories: [csharp, dotnetcore, swagger]
date: 2019-01-30 18:35:13 -0300
background: ''
subtitle: ''
---

É simples, rápido e fácil documentar suas aplicações com o swagger! Eu provo aqui:  
  
Primeiro adicione a referência **Swashbuckle.AspNetCore** no seu projeto.

<div>
  <row>
     <img src="/img/posts/sw2.gif" style="display: block; margin: 0 auto; width: 90%"> 
  </row>
</div>

Adicione no seu projeto a classe: **SwaggerServiceExtensions** com os métodos: AddSwaggerDocumentation e UseSwaggerDocumentation  

<div>
  <row>
     <img src="/img/posts/sw3.gif" style="display: block; margin: 0 auto; width: 90%"> 
  </row>
</div>
  
Adicione o método **AddSwaggerDocumentation** no método **ConfigureServices** da classe **Startup**   
Em seguida adicione o método **UseSwaggerDocumentation** no método **Configure** da classe **Startup** e confire em app.Run o swagger para ser a primeira rota acessada por sua aplicação.  

```javascript
public static class SwaggerServiceExtensions
    {
        public static IServiceCollection AddSwaggerDocumentation(this IServiceCollection services)
        {
            services.AddSwaggerGen(c =>
            {
                c.SwaggerDoc("v1", new Info { Title = "API One", Version = "v1" });
                c.IncludeXmlComments(Path.Combine(AppContext.BaseDirectory, "ApiOne.xml"));
            });

            return services;
        }

        public static IApplicationBuilder UseSwaggerDocumentation(this IApplicationBuilder app)
        {
            app.UseSwagger();
            app.UseSwaggerUI(c =>
            {
                c.SwaggerEndpoint("/swagger/v1/swagger.json", "API One v1");

                c.DocumentTitle = "API One ";
                c.DocExpansion(DocExpansion.None);
            });

            return app;
        }
    }
```  
  
Importante: Não se esqueça de habilitar a geração do xml de comentários.  

<div>
  <row>
     <img src="/img/posts/sw4.gif" style="display: block; margin: 0 auto; width: 90%"> 
  </row>
</div> 

### It Works!  
  
<div>
  <row>
     <img src="/img/posts/sw5.gif" style="display: block; margin: 0 auto; width: 90%"> 
  </row>
</div>
  

