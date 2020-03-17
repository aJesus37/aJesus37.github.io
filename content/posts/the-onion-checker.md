---
title: "The Onion Checker"
date: 2017-02-01T12:00:00-03:00
lastmod: 2020-03-17T10:10:00-03:00
description: "Uma introdução à ferramenta para automação de checagem de links na Deep Web"
categories: ["Deep Web"]
tags: ["Linux", "Tool", "HowTo"]

author: "Jesus"
authorLink: ""
license: ""

hiddenFromHomePage: false

featuredImage: "images/github-wallpaper.png"
featuredImagePreview: ""

toc: true
autoCollapseToc: true
math: true
lightgallery: true
linkToMarkdown: true
share:
  enable: true
comment: true
draft: false
---

Se você é um usuário "constante" da rede onion, está acostumado a encontrar diversos diretórios de links por lá, e acabar naquela dificuldade de ficar testando um por um, manualmente, não é? Pois bem, trago aqui algo que pode facilitar um pouco a sua navegação. 

Venho apresentar a ferramenta [__Onion Checker__](https://github.com/ajesus37/Onion-Checker), desenvolvida por mim.

O intuito dessa ferramenta é organizar links referentes à rede onion, bem como testar se os mesmos estão online, e caso positivo, adicionar o título existente no site, bem como o link, num txt.

A utilização base do programa é bem simples, sendo exatamente:

`onion-checker -c ListaDeLinks.txt`


Ou ainda utilizando um arquivo de destino para os links online. Caso seja omitido, os links online irão para a `$HOME` do usuário, no arquivo _linkson.txt_.

Uma interessante funcionalidade é a de permitir ao usuário escolher o tempo de timeout para a checagem dos links, para que os mesmos sejam dados como offline, em _segundos_, _minutos_, _horas_ e até _dias_.

![](https://i.imgur.com/Swa1aRf.png)

Dentre as outras funcionalidades do programa, pode-se salientar a de organização de links. Esse comando pega __N__ arquivos de texto contendo links passados para o programa, e os filtra, passando apenas os links, linha por linha, para outro arquivo ou para serem imprimidos na tela. O uso dessa função é:

`onion-checker -l Arquivo1.txt Arquivo2.txt Arquivo3.txt ArquivoDestino.txt`

O último nome passado será sempre o arquivo destino, e caso o último seja `-st`, o conteúdo será exibido na tela.

Outra função mais simples apenas une arquivos diferentes uns nos outros, sob a flag `-j`.

Abaixo você pode ver a mensagem completa de ajuda contento todos os comandos que o programa aceita, e para mais ajuda, use um deles sem flag alguma.

![](https://i.imgur.com/22LA8f2.png)

