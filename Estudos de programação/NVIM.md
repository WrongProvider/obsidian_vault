### 1. Movimentação Básica (Sem usar as setas)

No Neovim, as teclas de letras são mais rápidas que as setas porque sua mão não sai da posição de digitar.

- `h`, `j`, `k`, `l`: Esquerda, Baixo, Cima, Direita.
    
- `w`: Pula para o início da próxima **palavra** (word).
    
- `b`: Volta para o início da **palavra** anterior (back).
    
- `e`: Pula para o **fim** da palavra.
    
- `0` (zero): Vai para o início da linha.
    
- `$`: Vai para o fim da linha.
    
- `gg`: Vai para a primeira linha do arquivo.
    
- `G`: Vai para a última linha do arquivo.
    
- `:N`: (onde N é um número) vai direto para a linha N.
    

---

### 2. Edição "Cirúrgica" (Poder de Fogo)

- `u`: Desfazer (Undo).
    
- `Ctrl + r`: Refazer (Redo).
    
- `x`: Apaga o caractere sob o cursor.
    
- `dd`: Apaga (corta) a linha inteira.
    
- `dw`: Apaga da posição do cursor até o fim da palavra.
    
- `di(`: Apaga tudo o que está **dentro** dos parênteses. (Extremamente útil em Python!)
    
- `ca"`: Apaga tudo dentro das aspas **e** as aspas, entrando no modo de inserção.
    
- `yy`: Copia (yank) a linha.
    
- `p`: Cola (paste) depois do cursor.
    

---

### 3. Modos de Visualização (Seleção)

- `v`: Modo visual (seleciona caractere por caractere).
    
- `V` (Shift+v): Seleciona a **linha** inteira.
    
- `Ctrl + v`: Modo bloco (seleciona colunas – ótimo para apagar ou inserir em várias linhas).
    
- `gv`: Seleciona novamente o último bloco que você tinha selecionado.
    

---

### 4. Busca e Substituição

- `/termo`: Busca por "termo" no arquivo.
    
    - `n`: Vai para a próxima ocorrência.
        
    - `N`: Volta para a ocorrência anterior.
        
- `:%s/antigo/novo/g`: Substitui **todas** as palavras "antigo" por "novo" no arquivo inteiro.
    
- `:%s/antigo/novo/gc`: Substitui, mas **pergunta** antes de cada uma (mais seguro).
    

---

### 5. Atalhos que Criamos no seu `init.lua`

Estes dependem da sua configuração:

- `Espaço + e`: Abre/Fecha a árvore de arquivos.
    
- `Espaço + ff`: Busca arquivos pelo nome (Telescope).
    
- `Espaço + lg`: Busca palavras dentro de todos os arquivos (Live Grep).
    
- `gd`: Vai para a definição da função (LSP).
    
- `K`: Mostra a documentação da função sob o cursor.
    
- `gcc`: Comenta/Descomenta a linha atual.
    
- `Ctrl + o`: Volta para onde você estava antes do `gd`.
    
- `Espaço + rn`: renomear variaveis.

### 6. Comandos de "Saída de Emergência"

- `:w`: Salva o arquivo.
    
- `:q`: Sai do Neovim (se estiver salvo).
    
- `:q!`: Sai sem salvar (o famoso "estragou tudo, quero fechar").
    
- `:wq`: Salva e sai.
    

---

### Dica de Ouro: O "Operador de Número"

Quase todo comando no Neovim aceita um número antes.

- `5dd`: Apaga 5 linhas de uma vez.
    
- `10j`: Desce 10 linhas.
    
- `3w`: Pula 3 palavras para a frente.


|**Plugin**|**Comando**|**Função**|
|---|---|---|
|**Mason**|`:Mason`|Interface para instalar LSPs, Debuggers e Linters.|
|**Lazy**|`:Lazy`|Atualizar plugins ou ver se algo quebrou.|
|**Treesitter**|`:TSUpdate`|Atualiza os parsers de sintaxe instalados.|
|**Telescope**|`<leader>ff`|Busca arquivos no projeto (seu atalho personalizado).|
|**Telescope**|`<leader>lg`|Busca palavras dentro dos arquivos (Live Grep).|
|**LSP**|`:LspInfo`|Verifica se o LSP (ex: Pyright ou Gopls) está ativo no arquivo.|
