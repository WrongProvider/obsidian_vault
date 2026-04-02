`set advanced-firewall`

- `strict-policy` ->
    
    "When strict policy is applied, the device drops specific traffic and attacks such as the Winnuke attack, Land attack, Zero IP Protocol, and various other IP based attacks against the firewall.
    
    By default, strict policy is always on. To turn the strict policy on or off, in the console use the command: set advanced-firewall strict-policy on/off"
    
- `ftpbounce-prevention` ->"quando habilitado faz a prevenção desse tipo de ataque. Resumo do attaque: o source que estiver obfuscando seu ip e enviando o pacote para o servidor, como se fosse um MITM."
    
- `sys-traffic-nat` ->"o trafego gerado do firewallvai ser nateado, provavelmente pela regra reflexiva com o MASK."
    
- `tcp-frto` -> "algoritimo que onde funciona o wifi ele procura os pacotes mais eficientemente, ótimo para packet loss"
- `tcp-timestamp` -> "tcp timestamp melhora o calculo do roundtrip"