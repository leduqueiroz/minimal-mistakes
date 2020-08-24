---
layout: post
title: Async Main - C# 7.1
date: 2018-06-20 18:35:13 -0300
category: csharp
background: ''
subtitle: ''
---

Boa noite pessoal!  

Nessa série de posts vou listar algumas das melhorias disponíveis no C# 7.0 e superior bem como exemplos de utilização das mesmas, espero que seja útil para todos.  

### Async Main

A partir dessa versão do c# é possível que seu método **main** receba a instrução **await**. 
Isso faz com que o ponto de entrada de sua aplicação se torne assíncrono. 
Para isso basta que seu método retorne uma **Task<>** ou **Task<int>**  

#### Quando utilizar?

Um exemplo clássico para utilização do Async Main é para a leitura e escrita de arquivos, ou a leitura de um retorno de uma consulta REST:  

> ![an image alt text]({{ site.baseurl }}/img/posts/asyncmain.jpg "an image title")  

Referência: <https://docs.microsoft.com/pt-br/dotnet/csharp/whats-new/csharp-7-1>  

