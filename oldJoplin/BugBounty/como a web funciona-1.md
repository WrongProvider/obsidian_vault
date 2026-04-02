como a web funciona

https://www.hacker101.com/playlists/newcomers

http request

request header contem os seguintes parametros:

host: qual host vai manejar a request

accept: qual MIME type é aceito, geralemente usado para JSON ou XML output para web-services

cookie: passa dados de cookies para o server

referer: pagina que trouxe este request

authorization: basicamente usado para formas de auth basicas como &lt;base64´d user:passwd&gt;

Cokies -

são dados armazenados no cliente para alguma funcionalidade, eles sempre tem um periodo de existencia mesmo que alguns sejam longos.

segurança nos cookies:

pessoas tendem a esquecer de suprir os cookies para um determinado subdomíninio o que faz com que os hackers utilizem-no até nos roots "." dir fazendo coisas terriveis kkk.

Caso vc limite o cookie para ".teste.com", este so podera ser usado em todos os subdominios.

Agora se vc limitar por ".haha.teste.com", este so podera ser usado por subdominios tipo ".lul.haha.teste.com" ou outros, mas NÃO poderá ser usado em irmão como ".ye.teste.com"

setcookieheader:

duas flags importantes para os cookies:

secure: so pode ser usado em https

HTTPOnly:  não pode ser lido por javascript como "document.cookie" variable.

discrepansia no parseamento de html pode levar a quebras de segurança. Ex se um parser usar html4 e o Waf o 5 pode dar merda

![4173ab607a8fac081dcdaf9edfb93828.png](../_resources/4173ab607a8fac081dcdaf9edfb93828-1.png)

mime sniffing:

se o browser acha que aquilo é html ele vai parsear aquilo como html, então olhe imagem e arquivos contendo tags html são executadas pelo browser

enconde sniffing

tente controlar o jeito que o browser faz decoding para talvez alterar o jeito que ele faz o parsing

![c6d2f83a5207cdaf0ac1e730546452c1.png](../_resources/c6d2f83a5207cdaf0ac1e730546452c1-1.png)

sempre especificar MIME types

Same Origin Policy (SOP)

faz uma restrição sobre o que vc pode fazer de requisição como:

que dominios vc pode contactar via AJAX

[https://www.w3schools.com/XML/ajax\_xmlhttprequest\_send.asp](https://www.w3schools.com/XML/ajax_xmlhttprequest_send.asp)

acessar DOM (document object model) em frames/janelas separadas

o SOP é mais estrito do que o cookies pois ele limita coisas como:

tem que usar http/https, mesma porta 80 ou 443. Dominio tem que ter o match exato -- sem  * ou subdomain walking.

vc pode soltar um pouco o SOP document.domain em js

chrome extension usa post-messages os webdev quase nunca validam as mensagens

CORS (cross origin resource sharing)

permite criar request fora do SOP XMLHttpRequests

CSRF

ataque que faz a vitima se redirecionar para um site que o atacante controla, e dai o atacante manda dados para o site em ataque como se fosse a vitima.

![e9e109df1b43fa9784040e9b2c777db9.png](../_resources/e9e109df1b43fa9784040e9b2c777db9-1.png)

![80ea84e4fb8015886949881f4aa6159d.png](../_resources/80ea84e4fb8015886949881f4aa6159d-1.png)![1c27f990edd33d14374eecc68360d0b1.png](../_resources/1c27f990edd33d14374eecc68360d0b1-1.png)

CSRF TOKENS

Tipicamente quando vc usa um scanner de vuln em uma aplicação vai perceber que o GET muda o estado da aplicação o tempo todo. Então caso tenha o CSRF no POST e esteja ocorrendo mudança de estado em GET, isso está automaticamente QUEBRADO e vc pode exploitar

![41b1e4c22d0aec9553d43a2e0f6cb68f.png](../_resources/41b1e4c22d0aec9553d43a2e0f6cb68f-1.png)