Supplemental tools

OWASP ZAP e Nikto -> identificar endpoints

WFuzz e Arjun -> quando descobrir endpoints utilize-os para focar num ponto especifico e descobrir funcionalidades

Kiterunner -> content discovery de Endpoints, quando se trata de API o Kr é melhor do que o Dirb, Gobuster, etc

https://wordlists.assetnote.io/ -\> melhor lugar para pegar wordlists

# Wfuzz

wfuzz options -z payload,params url

exemplo:

wfuzz -z file,/usr/share/wordlists/list.txt http://targetname.com/FUZZ

especificando que o payload é um arquivo (file) com o path na /usr/share....

ex2:

wfuzz -z list,A-B-C -z range,1-3 http://targetname.com/FUZZ/user_id=FUZZ2

especificando 2 payloads do tipo range (1-3), e do tipo lista (A-B-C) para serem substituidos nas palavras FUZZ

use os seguintes para ter controle do output do e mostrar certos resultados FUZZ:

--sc  Only shows responses with specific HTTP response codes

--sl  Only shows responses with a certain number of lines

--sw  Only shows responses with a certain number of words

--sh  Only shows responses with a certain number of characters

e esses para esconder certos resultados:

--hc  Hides responses with specific HTTP status codes

--hl  Hides responses with a specified number of lines

--hw  Hides responses with a specified number of words

--hh  Hides responses with specified number of characters

-p  &lt;ip:port&gt; usa proxy (bom pra debuggar requests)

wfuzz -z file,/usr/share/wordlists/list.txt –sc 404 –sh 950 http://targetname.com/FUZZ

mostra so os 404, com o numero de caracteres entre 950

### bruteforce

wfuzz -d '{"email":"a@email.com","password":"FUZZ"}' --hc 405 -H 'Content-Type: application/json' -z file,/home/hapihacker/rockyou.txt http://192.168.195.130:8888/api/v2/auth

wfuzz -u vulnexample.com/api/v2/user/dashboard –hc 404 -H "token: Ab4dt0k3nFUZZFUZ2ZFUZ3Z1" -z list,a-b-c-d -z list,a-b-c-d -z range,0-9

### fuzzing deep

wfuzz -z file,/home/hapihacker/big-list-of-naughty-strings.txt -H "Content-Type: application/

json" -H "x-access-token: \[...\]" --hc 400 -X PUT -d "{

\\"user\\": \\"FUZZ\\",

\\"pass\\": \\"FUZZ\\",

\\"id\\": \\"FUZZ\\",

\\"name\\": \\"FUZZ\\",

\\"is_admin\\": \\"FUZZ\\",

\\"account_balance\\": \\"FUZZ\\"

}" -u http://192.168.195.132:8090/api/user/edit_info

wfuzz -e encoders -> monta uma lista de encoders a serem usados

se vc quiser passar diversos encoders na lista, é só separar pelo @ como no exemplo abaixo:

wfuzz -z list,aaaaa-bbbbb-ccccc,base64@random_upper -u http://192.168.195.130:8888/identity/api/auth/v2/FUZZ

# Arjun

arjun.py -u http://target_address.com

caso o target tenha um rate limit use ele com a seguinte opção:

arjun.py -u http://target\_address.com -o arjun\_results.json --stable

ele pega o conteudo no JSON

arjun --headers "Content-Type: application/json\]" -u http://192.168.15.130:8888/identity/api/auth/signup -m JSON --include='{$arjun$}'

# Kiterunner

da pra pegar as respostas do KR e jogar no replay para ele falar o que rolou no resultado.

![3ef7190ef5093ab892246c04d13fcd5b.png](../_resources/3ef7190ef5093ab892246c04d13fcd5b.png)

replay:

![3ea5c3b0c13e79a6361b1306d49b1066.png](../_resources/3ea5c3b0c13e79a6361b1306d49b1066.png)

kr scan -> usa o arquivo kite

kr brute -> usa uma wordlist qualquer

## usando o kiterunner com um header de auth

kiterunner scan http://192.168.184.129:8090 -A=apiroutes-240528 -H "x-access-token: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyIjp7Il9pZCI6NDUsImVtYWlsIjoidGVzdEBoYWNrZXIuY29tIiwicGFzc3dvcmQiOiJ0ZXN0ZUAxMjM0IiwibmFtZSI6InF1ZXN0aW9udGVybSIsInBpYyI6Imh0dHBzOi8vczMuYW1hem9uYXdzLmNvbS91aWZhY2VzL2ZhY2VzL3R3aXR0ZXIvdHVya3V0dXVsaS8xMjguanBnIiwiYWNjb3VudF9iYWxhbmNlIjo1MCwiaXNfYWRtaW4iOmZhbHNlLCJhbGxfcGljdHVyZXMiOltdfSwiaWF0IjoxNzE5MzExNTE1fQ.ddUG1ktcYLSiwSOt2AWNivs1zsmvwmTd7ayyibbdsDs" -o kr\_with\_token

# Fuzzing Repos

https://github.com/fuzzdb-project/fuzzdb

https://github.com/xmendez/wfuzz