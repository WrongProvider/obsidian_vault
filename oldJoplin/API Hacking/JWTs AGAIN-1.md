# JWTs AGAIN

## none alg

, se ver o alg como none é easy win

só remover a assinatura e colocar qualquer usuario que quiser

`jwt_tools -X a <token>`  gera diversos tokens com o algoritimo none

## Algorithm switch

faz um key-confusion attack, ele usa uma chave publica de um algorithm RSA256 (ex) transformando ele num HS256, usando a chave publica como uma chave privada, para tentar enganar o servidor.

jwt_tool -x k-pk &lt;public-key-pem&gt; &lt;jwt&gt;

## JWT Crack

usa o jwt_tool para crackear o segredo do token, usa mais o hashcat pq ele tem mais poder.

isso so funciona em chave privada, hmac HS256 da vida

jwt_tool &lt;jwt&gt; -C -d &lt;wordlist&gt;

### como achar chaves publicas do jwt:

https://github.com/ticarpi/jwt_tool/wiki/Finding-Public-Keys