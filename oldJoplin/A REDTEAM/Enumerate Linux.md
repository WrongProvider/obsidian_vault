release

&nbsp;lista os arquivos de conf de release

```shell-session
ls /etc/*-release
```

&nbsp;verifica qual é o SO

```shell-session
cat /etc/os-release
```

hostname

```shell-session
cat /etc/passwd
```

```shell-session
cat /etc/group
```

```shell-session
sudo cat /etc/shadow
```

Email

```shell-session
ls -lh /var/mail/
```

checa Aplicações instaladas

- `ls -lh /usr/bin/`
- `ls -lh /sbin/`
- `dpkg -l`
- `rpm -qa`

Mostra quem ta logado  
who  
userID  
whoami

id

last -> mostra o ultimo login do user

sudo -l -> lista os comandos

Mostra todos que estão logados no momento

```shell-session
w
```

DNS estatico do linux 

```shell-session
cat /etc/resolv.conf
```

mostra os arquivos abertos e o -i mostra as portas desses arquivos a 25 arquivos

```shell-session
sudo lsof -i :25
```

&nbsp;

**netstat -ltnp** (mostra o PID precisa rodar com o sudo)