comandos

* http.request -> apply as a collumn
* tls.handshake.type == 1 -> app
* frame constains "wireshark"

lembra de mexer na engrenagem no começo para criar automaticamente outro arquivo a cada 500 MB


pesquisar sobre tap ou span para redirecionar pacotes para um lugar onde o wireshark esteja instalado
profitap.com

capture packet -> captura o pacote e dai podemos fazer uma analisa

display filter -> analisa um pacote capturado

tcp.port in {80, 443, 53} mostra os pacotes das seguintes portas

frame contains google -> upercase e lowercase matters

frame matches Google -> case inssensitive

configurar name resolution em preferencias