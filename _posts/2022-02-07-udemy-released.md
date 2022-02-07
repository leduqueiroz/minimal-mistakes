---
layout: post
title: "Eventos de webhook"
subtitle: ".Net Core + AWS - Parte 1"
date: 2020-04-20 13:00:00 -0300
background: ''
---
<!DOCTYPE html>
<head>
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0/css/bootstrap.min.css" integrity="sha384-Gn5384xqQ1aoWXA+058RXPxPg6fy4IWvTNh0E263XmFcJlSAwiGgFAW/dAiS6JXm" crossorigin="anonymous">
</head>
<body
    <p>
	  <h2>Iniciando nossa biblioteca</h2>
	</p>
    <p>
	    Nesse artigo vamos criar uma estrutura com .Net core e os serviços da AWS para notificar eventos de webhook para determinadas urls 
		(posteriormente podemos incluir notificações para sockets, emails, etc).
    </p>
    <p>
        <b>1 -</b> Primeiramente vamos criar nosso projeto.
		<br>
		<b>2 -</b> O próximo passo é definir a estrutura dentro da nossa biblioteca criando as pastas:
		  <ul>
			  <li>Application</li>
			  <li>Controller</li>
			  <li>Domain</li>
			  <li>Infra</li>
          </ul>	
		<b>3 -</b> Crie a pasta Configuration e dentro da mesma uma outra chamada Internal.
		<br>
     	<b>4 -</b> Em Internal crie a interface IHookConfiguration com a seguinte estrutura:
		<div style="margin-top:15px; margin-bottom:15px">
		  <row>
			 <img src="/img/posts/hook/01.png"> 
		  </row>
		</div>
		<b>5 -</b> Em Internal crie também a interface ITopicAuth com a seguinte estrutura:
		<div style="margin-top:15px; margin-bottom:15px">
		  <row>
			 <img src="/img/posts/hook/02.png"> 
		  </row>
		</div>
		<b>6 -</b> Ainda em Internal crie a classe TopicAuth com a seguinte estrutura:
		<div style="margin-top:15px; margin-bottom:15px">
		  <row>
			 <img src="/img/posts/hook/03.png"> 
		  </row>
		</div>
		<b>7 -</b> Finalizando, ainda em Internal, crie a classe HookConfiguration com a seguinte estrutura:
		<div style="margin-top:15px; margin-bottom:15px">
		  <row>
			 <img src="/img/posts/hook/04.png"> 
		  </row>
		</div>
		<b>8 -</b> Em Configuration crie a classe HookConfigurationBuilder com a seguinte estrutura:
		<div style="margin-top:15px; margin-bottom:15px">
		  <row>
			 <img src="/img/posts/hook/05.png"> 
		  </row>
		</div>
		Vamos utilizar o padrão conhecido como <b><a href="https://garywoodfine.com/the-builder-pattern-net-core/">Builder Pattern</a></b> 
		para recuperar os dados do app.settings e configurar a nossa biblioteca.
		<div style="margin-top:15px; margin-bottom:15px">
		  <row>
			 <img src="/img/posts/hook/01.gif" style="display: block; margin: 0 auto; width: 90%"> 
		  </row>
		</div>
		<br>
    </p>
	<p>
	  <b>9 -</b>  Para finalizar a primeira parte vamos criar a classe WebHookExtensions com a seguinte estrutura:
	  	<div style="margin-top:15px; margin-bottom:15px">
		  <row>
			 <img src="/img/posts/hook/06.png"> 
		  </row>
		</div>
		Nesse ponto para qualquer outra aplicação utilizar nossa biblioteca de notificações por webhook 
		basta adicionar o método AddWebHook() no Startup. 
	</p>
	<p>
	   Na próxima parte vamos configurar as camadas da Controller, Application, Domain e Infra da nossa biblioteca.	  
	</p>
	<p>
	  <h2> Abraços e até lá!</h2>
	</p>
</body>
