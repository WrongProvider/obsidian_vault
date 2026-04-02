IPSEC LEMBRAR* 

sempre que for fazer vpn pergunte o maximo de coisas para não ser surpreendido, tenha uma topologia e quais serviços o outro lado vai poder acessar. No fortigate, quando a vpn ipsec é criada, o fortigate produz as rotas -- isso se estiver descrito quais redes vão ser acessadas --, agora se estiver em 0.0.0.0 na fase 2, e o que quer se conectar precisar acessar outros ambientes conectados ao seu ambiente. Vc pode fazer de duas maneiras:
 1- criar uma rota estática para o conectado.
 2- criar uma SNAT para que o conectado tenha o mesmo IP que sua rede local. E com isso ter acesso ao IPsec de outros ambientes.