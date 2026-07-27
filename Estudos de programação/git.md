
git status
git diff

git add .
git commit
git push

git stash
git pull


git diff --staged
git log --oneline


```
git checkout main
# ou, em versões mais novas:
git switch main
```
```
git pull origin main
```
```
git merge nome-da-sua-branch
```
```
git push origin main
```



```
# 1. Salve ou certifique-se de que seus arquivos de ambiente (.env, etc.) estão seguros
# (caso estejam dentro da pasta deploy ou raiz, verifique se estão no .gitignore)

# 2. Descarta todas as alterações locais rastreadas
git reset --hard HEAD

# 3. Remove arquivos e pastas não rastreadas (limpeza profunda)
# O '-fd' apaga diretórios e arquivos untracked. Use '-n' antes se quiser simular o que será apagado.
git clean -fd

# 4. Agora sim, puxe a versão mais recente da main sem conflitos
git pull origin main
```


```
# 1. Guarda alterações locais e limpa a árvore de trabalho temporariamente
git stash -u

# 2. Puxa a versão atualizada da main
git pull origin main

# 3. (Opcional) Se precisar recuperar algo que estava no stash:
# git stash pop
```