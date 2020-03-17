---
title: "Tor Browser as a Browser"
date: 2019-03-21T20:00:00-03:00
lastmod: 2020-03-17T10:13:20-03:00
description: "Esqueçamos a rede onion, hidden services e tudo mais. O que o Tor pode fazer, como um navegador comum?"
tags: ["Tor"]
categories: ["Deep Web"]
author: "Jesus"
authorLink: ""
license: ""

hiddenFromHomePage: false

featuredImage: "images/tor-wallpaper.png"
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

Quando se trata de *Tor*, geralmente não se fazem distinções, *Tor* é único, *Tor* é o todo, mas nos enganamos ao pensar dessa forma.
O *Tor*, falando de forma pura e simples, é um composto de duas partes. O _Tor_ _**Browser**_, e o _Tor **Network**_. Os nomes são um tanto auto-explicativos, mas trata-se do **navegador**, a interface gráfica e meio entre o usuário e a **rede**, que é onde a magia dos *hidden services* e conceitos mais complexos da segurança do *Tor* se aplicam.

Nesse artigo tratarei exclusivamente daquilo que cobre o navegador, ou seja, não irei abordar aspectos técnicos da rede, que na maioria massiva dos casos, está diretamente atrelada.

## Ignorando a rede, o *Tor Browser* é apenas um Firefox comum?

**De forma alguma**. Essa afirmação está muito longe de estar correta.
O *Tor Browser* é uma implementação **customizada** do Firefox[^1]. O Firefox, por sua vez é um navegador de código aberto, que preza pela privacidade de seus usuários, o que o faz a melhor escolha para os fins do *Tor*.
Acima dele, são implementadas não somente customizações, como também configurações específicas. O Projeto *Tor* leva muito mais a sério a privacidade e segurança do que o Firefox, afinal esse é o intuito do projeto, dessa forma, traz configurações que não trazem melhor navegabilidade ou uma melhor experiência de usuário, mas traz aquilo que se propõe: **privacidade e segurança**.

Dentre as alterações contidas nas configurações[^2], podemos citar o bloqueio à escrita de histórico, isolamento de *downloads*, o não *cache* de informações como *logins* e informações em formulários, bem como configurações padrão de segurança, como testes de *malware*, *phishing* e afins. As configurações também não são sincronizadas, para que nada da sua navegação seja salva na nuvem. Define também várias configurações *'default'* de *fingerprinting*, para que o computador/*hardware* do usuário não possa ser identificado, além de bloquear conteúdo de terceiros e definir os *proxies* para a própria rede, dentre outras informações, como correções de *bugs* que poderiam afetar a segurança de alguma forma.

Ele vem com o *TorButton*[^3], que garante que as requisições de *DNS* são de fato enviadas para a rede *Tor* (caso você pense em usar a rede num navegador qualquer, saiba que corre o risco de sofrer *DNS Leak*[^4]).

O navegador vem por padrão com as extensões *HTTPS-Everywhere*[^5], bem como o *NoScript*[^6]. O primeiro garante que a grande maioria das requisições trafegue criptografada (tratando dentro da rede *Tor*, isso previne que nós de saída espiem o tráfego que passa por elas). Já o segundo, garante que por padrão, nenhum *script* seja executado, a menos que a *URL* seja definida numa *whitelist* para tal. Além disso, mais que apenas vir com elas instaladas, elas são otimizadas para maximização da segurança e privacidade do usuário (o que por vezes, diminui ou acaba com a usabilidade, especialmente tratando-se do *NoScript*).

O navegador também traz consigo requisitos de segurança e privacidade, como seguem:

### Segurança

Os requisitos de segurança são à princípio ligados à garantia de segurança do *Tor*.

1. **Obediência ao Proxy:**[^7] O navegador não deve sobrepor o *proxy* do *Tor* para conteúdo algum.
2. **Separação de estado:**[^8] O navegador não deve prover conteúdo que venha de nenhum outro navegador, ou de um modo de navegação que não o do próprio *Tor*. Isso inclui *plugins* independentes e estado compartilhado de implementações de sistema operacional do *TLS* e outras bibliotecas de suporte.
3. **Evitar o disco:**[^9] O navegador não deve escrever nenhuma informação que seja proveniente de, ou revele os dados de navegação para o disco, ou guardar em memória por tempo superior ao de navegação, a menos que o usuário explicitamente o tenha definido para tal.
4. **Isolamento de dados de aplicação:**[^10] Os componentes envolvidos em prover a navegação privada devem ser auto-contidos, ou devem prover um mecanismo para a rápida e completa remoção de evidências do modo de uso. Em outras palavras, o navegador não deve escrever ou fazer o sistema operacional escrever **qualquer informação** da navegação para o disco fora do controle da aplicação.

### Privacidade

Os requisitos de privacidade estão ligados com a redução da "habilidade de *linkagem*": A habilidade de de conectar a atividade de um usuário em um *site*, em outro *site* sem seu conhecimento ou consentimento explícito.

1. **Inviabilidade de conexão entre origens cruzadas:**[^11] As atividades em uma *URL* não devem poder ser conectadas às atividades em uma outra *URL* por nenhuma ferramenta automatizada de terceiros ou sem a interação ou aprovação do usuário. Essa conectividade é especifica para os casos de identificadores armazenados, *tokens* de autenticação e estado compartilhado.

2. **Inviabilidade de fingerprinting de origens cruzadas:**[^12] Exatamente como o primeiro ponto, mas especificamente para atributos de *fingerprinting* das ações do navegador.

3. **Inviabilidade de conexões de longo período:**[^13] O navegador deve trazer uma forma óbvia e fácil para o usuário de remover todos os seus *tokens* de navegação e estado do navegador para obter uma nova identidade. Adicionalmente, o navegador deve limpar qualquer estado que viabilize conexão de comportamento por padrão, automaticamente ao reiniciar o navegador, a menos que o usuário opte pelo contrário.

## O Fim? Talvez.

Falar de segurança e privacidade é um tanto complexo, visto que é um tema muito amplo de delicado, sem citar complexo. Por esse motivo, não irei tratar de **todos** os pontos desse navegador, mas deixo aqui[^14] o link para a documentação do *Tor*, que me serviu de base para esse artigo. Sinta-se livre para aprofundar-se no assunto, ou tirar dúvidas na seção de comentários abaixo.

Quem sabe em breve não surja uma parte dois para esse conteúdo, não é mesmo?
Até a próxima. ;)


## Bibliografia

[^1]:https://www.mozilla.org/firefox/new/
[^2]:https://gitweb.torproject.org/tor-browser.git/tree/browser/app/profile/000-tor-browser.js?h=tor-browser-52.5.2esr-7.0-2]
[^3]:https://gitweb.torproject.org/torbutton.git/
[^4]:https://en.wikipedia.org/wiki/DNS_leak
[^5]:https://www.eff.org/https-everywhere
[^7]:https://www.torproject.org/projects/torbrowser/design/#proxy-obedience
[^8]:https://www.torproject.org/projects/torbrowser/design/#state-separation
[^9]:https://www.torproject.org/projects/torbrowser/design/#disk-avoidance
[^10]:https://www.torproject.org/projects/torbrowser/design/#app-data-isolation
[^11]:https://www.torproject.org/projects/torbrowser/design/#identifier-linkability
[^12]:https://www.torproject.org/projects/torbrowser/design/#fingerprinting-linkability
[^13]:https://www.torproject.org/projects/torbrowser/design/#new-identity
[^14]:https://www.torproject.org/projects/torbrowser/design/
