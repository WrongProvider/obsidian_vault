**Administrators** -> usuarios mais privilegiados, podem mudar qualquer config do sistema e acessar qualquer arquivo

**Standard Users** \-> limitado

**SYSTEM / LocalSystem** -> conta do SO, tem acesso total, e na maioria mais poder que o Admin

**Local Service** -> roda serviços localmente com o privilegio minimo, usa conexões anonimas para rede

**Network Service** -> conta padrão do windows para rodar serviços com o menor dos privilegios. Vai usar as credenciais do pc para autenticar na rede.