vim

:%s />/\\r/g

entra em modo de substituicao, substitui todos os > por carrieage return (nova linha) em todas as aparições (g)

remove ANSI (cor) dos arquivos:

```
`:s/\%x1b\[[0-9;]*m//g`

```