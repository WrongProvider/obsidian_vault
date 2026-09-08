
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


# Verificar estado
git status
git branch --show-current

# Criar backup
git branch backup/minha-branch

# Guardar alterações locais
git stash push --include-untracked -m "backup das alterações locais"

# Atualizar referências remotas
git fetch origin main

# Criar branch limpa baseada na main
git switch -c feature/rands/obito-checkauto origin/main

# Reaplicar somente seu commit
git cherry-pick f41e5298

# Resolver conflito manualmente e marcar como resolvido
git add caminho/do/arquivo.py
git cherry-pick --continue

# Cancelar o cherry-pick, se necessário
git cherry-pick --abort

# Verificar resultado
git status
git rev-list --left-right --count origin/main...HEAD

git stash list
git stash pop stash@{0}

apos resolver conflito
git add arquivo-resolvido.py
git commit



#cherrypic
git -c core.editor=true cherry-pick --continue 2>&1 | tail -8