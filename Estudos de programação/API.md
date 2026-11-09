
RPC -> remote procedure call
usado para quando queremos uma "api local" dentro do ambiente do usuário (um binário é usado)

RMI -> remote method invocation (não mais usado)

REST ->http mais usado

## API defense

##### STRIDE

- Spoofing--Pretending to be somebody else
    
- Tampering--Altering data, messages, or settings you’re not supposed to alter
    
- Repudiation--Denying that you did something that you really did do
    
- Information disclosure--Revealing information that should be kept private
    
- Denial of service--Preventing others from accessing information and services
    
- Elevation of privilege--Gaining access to functionality you’re not supposed to have access to


CORS

só é interessante quando existe chamada da API direto do frontend de um browser. Agora se for tudo de servidor para servidor não é necessário. Quando implementado também estamos setando uma SOP (same-origin policy)

![[Pasted image 20261105171324.png]]![[Pasted image 20261105171338.png]]![[Pasted image 20261105171358.png]]

### Webauthn

da para pedir Fifo, Windows Hello etc. É uma api para autenticação multifator, bastante usada para validar os usuários com o padrão (What you know, _What you have_ e _What you are_). MFA


https://webauthn.guide/