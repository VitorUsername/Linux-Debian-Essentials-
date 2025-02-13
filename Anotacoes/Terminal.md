# Anotações Linux

 PREFÁCIO

- Fundamentos do Shell e Comandos Básicos [ir para o dia 02](#day-02)
- Comandos Avançados e Comandos Internos/Externos[ir para o dia 03](#day-03)
- Comandos Diversos [ir para o dia 04](#day-04)






<a id="day-02"></a>

# 📌 **DAY 2**


## **Comandos**

### **Visualização e Navegação**

```sh
cat          # Exibe o conteúdo de arquivos
pwd          # Mostra o diretório atual
ls           # Lista os arquivos e diretórios
ls -a        # Lista todos os arquivos, incluindo ocultos
ls -al       # Lista com permissões e dono
ls -lha      # Mostra o tamanho dos arquivos de forma legível
cd           # Vai para o diretório home
cd ~         # Volta para o diretório home
cd -         # Retorna ao diretório anterior
cd ..        # Sobe um nível na hierarquia de diretórios
cd /         # Vai para o diretório raiz
```

### **Histórico de Comandos**
```sh
history      # Exibe o histórico de comandos
# Setas para cima e para baixo também permitem navegar pelo histórico
```

### **Comandos de Usuário e Permissões**
```sh
su -         # Troca para o superusuário
```

### **Comandos de Arquivos e Diretórios**
```sh
echo "texto" > arquivo.txt  # Escreve "texto" dentro do arquivo
cat arquivo.txt             # Exibe o conteúdo de um arquivo
```

### **Atalhos de Terminal**
```sh
CTRL + L       # Limpa a tela
CTRL + D       # Sai do terminal
SHIFT + PGUP   # Rola para cima
SHIFT + PGDOWN # Rola para baixo
```

### **Troca de Shell**
```sh
cat /etc/shells  # Lista os shells disponíveis
```

### **Shutdown e Reboot**
```sh
halt            # Desligar a máquina
reboot          # Reiniciar a máquina
shutdown -h now # Desligar imediatamente
shutdown -r now # Reiniciar imediatamente
poweroff        # Desligar a máquina
init 0          # Desligar
init 1          # Modo de manutenção
shutdown -h 20:00   # Agendar desligamento às 20:00
shutdown -r +30     # Reinicia em 30 minutos
shutdown -c "msg"   # Cancela o desligamento programado e exibe uma mensagem
```

---

## **Explicações**

### **Interpretação do Prompt**
- `~$` → Usuário normal no diretório home (`/home/vitor`)
- `$` → Usuário normal
- `~#` → Superusuário no diretório `/root`
- `#` → Superusuário ativo

### **Arquivos e Parâmetros**
- Arquivos ocultos começam com `.` (ex: `.profile`)
- `-` (hífen) indica que estamos passando um parâmetro para um comando

### **Pipe e Paginação**
```sh
ls -a | grep 'arquivo'  # Busca arquivos específicos
ls -a | more            # Exibe página por página (barra de espaço para avançar)
ls -a | less            # Exibe página por página (setas para navegar, 'q' para sair)
```

---

## **Diretórios e Estrutura do Sistema**

### **Nomenclatura de Diretórios**
- `.` → Diretório atual
- `..` → Diretório anterior
- `/` → Diretório raiz
- Caminho absoluto: começa com `/` (ex: `/tmp/pasta`)
- Caminho relativo: sem `/` no início (ex: `cd .profile`)

### **Tipos de Arquivos e Permissões**
- `drwx-----` → Diretório
- `-rw-----` → Arquivo comum de texto
- `lrwxr----` → Link simbólico
- `brwxr----` → Dispositivo de bloco (ex: armazenamento)
- `crwxr----` → Dispositivo de caractere (ex: comunicação de dados)

### **Partições**
- `sda` → Primeiro disco
- `sda1` → Primeira partição do primeiro disco
- `sdb` → Segundo disco
- `sdc` → Terceiro disco
- Apenas 4 partições primárias por disco, o restante será lógico (`sda5`, `sda6`, etc.)

### **Estrutura de Diretórios (FHS)**

| Diretório  | Descrição |
|------------|-----------|
| `/bin` | Binários essenciais |
| `/sbin` | Binários administrativos (superusuário) |
| `/boot` | Arquivos de inicialização do sistema |
| `/dev` | Dispositivos do sistema (ex: `sda`, `tty`, etc.) |
| `/etc` | Configurações do sistema |
| `/home` | Diretórios pessoais dos usuários |
| `/lib` | Bibliotecas essenciais para `/bin` e `/sbin` |
| `/mnt` | Ponto de montagem temporário |
| `/media` | Ponto de montagem de mídias removíveis |
| `/opt` | Software instalado manualmente |
| `/proc` | Informações sobre processos do sistema |
| `/root` | Diretório pessoal do superusuário |
| `/tmp` | Arquivos temporários |
| `/usr` | Binários e bibliotecas adicionais |
| `/var` | Dados variáveis do sistema (logs, caches, emails, etc.) |

---
<a id="day-03"></a>

# 📌 DAY-3:COMANDOS INTERNOS E EXTERNOS NO LINUX


## COMANDOS INTERNOS (BUILT-IN COMMANDS)
Os comandos internos são embutidos no próprio shell, como o Bash. Eles são carregados na memória assim que o shell inicia e não precisam de arquivos externos para serem executados.

### Exemplos de comandos internos:
- `cd` → Muda o diretório atual.
- `echo` → Exibe texto no terminal.
- `pwd` → Mostra o diretório atual.
- `export` → Define variáveis de ambiente.
- `alias` → Cria atalhos para comandos.
- `exit` → Fecha o terminal.

### Vantagens:
- Como são carregados na memória, são mais rápidos que os comandos externos.

---

## COMANDOS EXTERNOS
São programas armazenados no sistema de arquivos e executados pelo shell. Para funcionar, o sistema precisa localizar o binário correspondente no `PATH` e carregá-lo na memória.

### Exemplos de comandos externos:
- `ls` → Lista arquivos e diretórios.
- `cat` → Exibe o conteúdo de arquivos.
- `grep` → Filtra texto com base em padrões.
- `find` → Busca arquivos no sistema.
- `tar` → Compacta e descompacta arquivos.
- `nano` → Editor de texto no terminal.

### Vantagens:
- São mais flexíveis e podem ser substituídos ou atualizados sem alterar o shell.

---

## COMO SABER SE UM COMANDO É INTERNO OU EXTERNO?

Use `type` para identificar o tipo de comando:
```bash
 type cd  # Comando interno
 type ls  # Comando externo
```

Use `which` para verificar se um comando tem um binário associado (se tiver, é externo):
```bash
 which ls  # Retorna /bin/ls (é externo)
 which cd  # Não retorna nada (é interno)
```

---

## ENTENDENDO A VARIÁVEL `PATH`
A variável `PATH` contém a lista de diretórios onde o shell procura por comandos externos.

```bash
 echo $PATH
```

Saída esperada:
```
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
```
Isso significa que quando um comando é digitado, o shell busca por ele nesses diretórios, na ordem listada.

Exemplo:
1. Digite `ls`.
2. O shell verifica se é um comando interno.
3. Se não for, busca nos diretórios listados no `PATH`.
4. Se encontrar, executa. Se não, retorna erro:
```bash
bash: comando_inexistente: comando não encontrado
```

---

## COMANDOS APRENDIDOS NO DIA 3

### Comandos básicos
- `echo` → Exibe um texto no terminal.
- `$PATH` → Mostra a lista de diretórios onde o shell procura por comandos.
- `echo $PATH` → Exibe os diretórios do `PATH`.
- `alias` → Cria atalhos para comandos.
- `which [comando]` → Encontra o caminho do binário de um comando externo.
- `type [comando]` → Identifica se um comando é interno ou externo.

---

## COMANDOS DE MANIPULAÇÃO DE DIRETÓRIOS

### Criar diretórios
```bash
mkdir nova_pasta         # Cria um diretório
mkdir -p dir1/dir2/dir3  # Cria múltiplos diretórios em cascata
```

### Listar diretórios
```bash
ls           # Lista arquivos e diretórios
ls -a        # Lista arquivos ocultos
ls -l        # Exibe detalhes dos arquivos
ls -t        # Ordena por tempo de modificação
ls -r        # Lista em ordem reversa
ls -r        # Ordem reversa.
ls -F        # Adiciona símbolos para diferenciar tipos de arquivos.
ls -lh       # Exibe o tamanho dos arquivos em formato legível.
ls -1        # Exibe os arquivos em uma lista vertical.
```

### Exibir estrutura de diretórios
```bash
tree -A  # Exibe estrutura em árvore
```

### Remover diretórios
```bash
rmdir pasta_vazia       # Remove diretório vazio
rmdir -p dir1/dir2/dir3 # Remove estrutura de diretórios vazios
```

---

## COMANDOS DE MANIPULAÇÃO DE ARQUIVOS

### Criar arquivos
```bash
touch arquivo.txt   # Cria um arquivo vazio.
touch .oculto       # Cria um arquivo oculto.
touch backup~       # Indica um arquivo de backup.
touch script*       # Indica um executável.
```

### Exibir conteúdo de arquivos
```bash
cat arquivo.txt      # Exibe o conteúdo de um arquivo
cat -n arquivo.txt   # Exibe o conteúdo numerando as linhas
cat -s arquivo.txt    # Oculta linhas em branco repetidas.
cat -b arquivo.txt   # Numera apenas linhas com conteúdo.
cat -e arquivo.txt   # Adiciona $ no final das linhas.
cat -T arquivo.txt   # Exibe tabulações como ^I.
cat -A arquivo.txt   # Exibe todos os caracteres ocultos.
```

### Copiar arquivos
```bash
cp origem destino     # Copia um arquivo
cp -r dir1 dir2       # Copia diretórios recursivamente
cp -u arquivo destino # Copia apenas se for mais recente
cp -v origem destino  # Mostra detalhes da cópia.
cp -a origem destino  # Copia arquivos e diretórios preservando atributos.
cp -p origem destino  # Preserva as permissões e timestamps.
```

### Mover e renomear arquivos
```bash
mv arquivo1 arquivo2  # Renomeia um arquivo
mv arquivo pasta/     # Move arquivo para outra pasta
mv -i arquivo pasta/ # Pede confirmação antes de substituir
```

### Remover arquivos
```bash
rm arquivo.txt        # Remove um arquivo
rm -r pasta/          # Remove um diretório e seu conteúdo
rm -rf pasta/         # Remove sem confirmação
rm -i arquivo.txt     # Pede confirmação antes de remover.
rm -- -arquivo        # Remove arquivos que começam com -.
```

---

## EDITORES DE TEXTO NO TERMINAL
- **nano** → Simples e fácil de usar.
- **vim** → Mais avançado, útil para programadores.

Para abrir um arquivo no `nano`:
```bash
nano arquivo.txt
```
Para salvar e sair do `nano`:
1. Pressione `CTRL + X`.
2. Digite `Y` e pressione `ENTER`.

Para abrir um arquivo no `vim`:
```bash
vim arquivo.txt
vim -b → Abre o arquivo em modo binário.
vim -r → Recupera arquivos corrompidos.
vim -y → Abre o arquivo em modo somente leitura.
vim -o → Abre arquivos em split (divisão de tela).
vim -O → Abre arquivos em split vertical.

```
Para sair do `vim`:
1. Pressione `ESC`.
2. Digite `:wq` e pressione `ENTER`.
---

<a id="day-04"></a>
# 📌 Linux - Anotações do Curso (Dia 04)

Esta é uma compilação completa dos comandos e parâmetros anotados no Dia 04. Confira cada seção para se familiarizar com os conceitos e comandos do Linux!

---

## 🔹 Curingas e Caracteres Especiais

### ✨ Asterisco `*`
- **Função:** Identifica nenhum, um ou mais caracteres em determinada posição.
- **Exemplos:**
  - `ls a*` → Lista arquivos que iniciam com a letra "a" (seguido de zero, um ou mais caracteres).
  - `ls *path` → Lista arquivos que terminam com a sequência "path".
  - `ls a*t` → Lista arquivos que começam com "a" e terminam com "t".

### ❓ Interrogação `?`
- **Função:** Representa exatamente 1 caractere em uma posição específica.
- **Exemplos:**
  - `ls m??` → Busca comandos com exatamente 3 caracteres (começando com "m").
  - `ls a?t*` → Procura comandos que têm um caractere entre "a" e "t", seguido de zero ou mais caracteres.
  - `ls ?z*` → Busca comandos que iniciam com qualquer caractere, possuem "z" no meio e terminam com zero ou mais caracteres.

### 🔲 Colchetes `[]`
- **Função:** Delimita um conjunto ou intervalo de caracteres.
- **Exemplos:**
  - `ls a[a-z]` → Seleciona arquivos que iniciam com "a" seguidos de qualquer letra de "a" a "z".
  - `ls m[^a-b]` → Busca arquivos que começam com "m" mas cujo caractere seguinte não seja "a" ou "b".

### 🔧 Chaves `{}`
- **Função:** Define padrões de strings onde é possível especificar alternativas.
- **Exemplo:**
  - `ls x{zd,ze}*` → Procura comandos que começam com "x", possuem "zd" ou "ze" como sequência e terminam com nenhum, um ou mais caracteres.

---

## 🔹 Comandos Gerais e Utilitários

### 🖥️ Limpar Tela e Comentários
- `clear` ou `CTRL+L` → Limpa a tela do terminal.
- `#` → Indica um comentário em scripts ou no terminal.

---

## 📅 Comando `date`

- **Exibir Data/Hora Atual:**
  - `date`
- **Configurar Data Completa:**
  - `date 101008452025`
    - *Formato:* Mês, Dia, Hora, Minuto, Ano (todos juntos).
- **Alterar Apenas o Horário:**
  - `date -s 08:30`
- **Salvar Alterações no Hardware Clock:**
  - `hwclock --systohc`
- **Formatar Saída com `date +%`:**
  - `date +%d` → Exibe apenas o dia.
  - `date +%d%Y` → Exibe dia seguido do ano completo (sem separador).
  - `date +%d-%m-%Y` → Exibe data formatada com separadores.
  - `date +"%d-%m-%Y %T"` → Exibe data e hora com um formato amigável.
  - `date +%j` → Mostra o dia do ano.
  - `date +%r` → Exibe o horário completo (padrão 24h).
  - `date +%p` → Indica se é AM ou PM.

---

## 📊 Comando `df` (Espaço em Disco)

- `df` → Mostra o espaço livre em cada partição montada.
- **Opções:**
  - `df -h` → Exibe em formato legível (human readable).
  - `df -H` → Utiliza tamanho comercial.
  - `df -l` → Lista somente sistemas de arquivos locais.
  - `df -m` → Exibe espaço em megabytes.
  - `df -a` → Exibe o pseudo file system com detalhes.
  - `df -i` → Mostra o uso de inodes (quantidade de pastas e arquivos criados).
  - `df -T` → Exibe o tipo de sistema de arquivos usado em cada partição.
  - `df -t taltal` → Filtra para exibir apenas um sistema de arquivos específico.

---

## 🔗 Comando `ln` (Criando Links)

- **Hardlink:**
  - `ln /bin/ls ls1`
    - *Observação:* Requer super usuário. Cria um link para `/bin/ls` com o nome `ls1`. Ao listar com `ls -l`, o arquivo aparecerá com 2 inodes, pois é referenciado duas vezes.
- **Link Simbólico:**
  - `ln -s /usr/bin link-do-ls`
    - *Observação:* Cria um link simbólico, que pode apontar para diretórios ou arquivos.
- **Cópia com Hardlink (via `cp -l`):**
  - `cp -rvl /usr /tmp/usr-link`
    - Cria uma cópia do diretório `/usr` utilizando hardlinks para reduzir o espaço.

---

## 📁 Comando `du` (Uso de Disco)

- **Exibir em Formato Humano:** `du -H`
- **Usando Blocos de 1024:** `du -h`
- **Resumo Total:** `du -s`
- **Em Kilobytes:** `du -k`
- **Em Megabytes:** `du -m`
- **Exibir Inodes:** `du --inodes -s`

---

## 🔍 Comando `find` (Busca de Arquivos e Diretórios)

**Sintaxe Geral:**
find [caminho] [opções] [expressão]
- **Por Nome:**
  - `find /caminho -name "arquivo.txt"`
  - `find /caminho -iname "arquivo.txt"` *(Ignora maiúsculas/minúsculas)*
- **Por Tipo:**
  - `find /caminho -type f` → Arquivos.
  - `find /caminho -type d` → Diretórios.
- **Por Tamanho:**
  - `find /caminho -size +10M`
    - *Use:* c (bytes), k (kilobytes), M (megabytes) ou G (gigabytes).
- **Por Usuário e Grupo:**
  - `find /caminho -user nome_usuario`
  - `find /caminho -group nome_grupo`
- **Por Permissões:**
  - `find /caminho -perm 755`
- **Por Data (Modificação, Acesso, Status):**
  - `find /caminho -mtime -7` → Arquivos modificados nos últimos 7 dias.
  - `find /caminho -atime +30` → Arquivos acessados há mais de 30 dias.
  - `find /caminho -ctime -1` → Arquivos com status alterado nas últimas 24 horas.
- **Excluir Arquivos Encontrados:**
  - `find /caminho -name "*.bak" -delete`
- **Controlar Profundidade da Busca:**
  - `find /caminho -maxdepth 2 -name "*.txt"` → Limita a profundidade máxima.
  - `find /caminho -mindepth 2 -name "*.txt"` → Define a profundidade mínima.

---

## 🖥️ Comando `free` (Memória do Sistema)

```bash
#Exibe informações sobre a memória física (RAM), swap e buffers/caches:
        total     used     free    shared  buff/cache  available
Mem:    7.8G      2.1G     3.2G    92M     2.4G        5.3G  
Swap:   2.0G      0B       2.0G
```
- **Outras Opções:**
  - `free -b`, `free -k`, `free -m`, `free -g` → Exibe a memória em bytes, kilobytes, megabytes ou gigabytes, respectivamente.
  - `free -h` → Exibe de forma legível (com sufixos como B, K, M, G).
  - `free -s 5` → Atualiza as informações a cada 5 segundos.
  - `free -t` → Adiciona uma linha total ao final da saída.
  - `free -c 3` → Executa o comando 3 vezes.

---

## 🔎 Comando `grep` (Busca de Texto em Arquivos)

- `grep -i "padrão" arquivo.txt` → Ignora a diferença entre maiúsculas e minúsculas.
- `grep -v "padrão" arquivo.txt` → Exibe linhas que **não** correspondem ao padrão.
- `grep -r "padrão" /caminho/do/diretorio` → Busca recursivamente em diretórios.
- `grep -l "padrão" *.txt` → Lista apenas os nomes dos arquivos que contêm o padrão.
- `grep -n "padrão" arquivo.txt` → Exibe os números das linhas junto às correspondências.
- `grep -c "padrão" arquivo.txt` → Conta o número de linhas que correspondem ao padrão.
- `grep -A 3 "padrão" arquivo.txt` → Exibe 3 linhas **após** a linha correspondente.
- `grep -B 3 "padrão" arquivo.txt` → Exibe 3 linhas **antes** da linha correspondente.
- `grep -C 3 "padrão" arquivo.txt` → Exibe 3 linhas antes **e** depois da correspondência.

---

## 📜 Comando `head` (Exibir Início do Arquivo)

- `head arquivo.txt` → Exibe as primeiras 10 linhas (padrão).
- `head -n 5 arquivo.txt` → Exibe as primeiras 5 linhas.
- `head -c 20 arquivo.txt` → Exibe os primeiros 20 caracteres.
- `head -q arquivo1.txt arquivo2.txt` → Exibe as primeiras 10 linhas de cada arquivo, sem imprimir os nomes.
- `head -v arquivo1.txt arquivo2.txt` → Exibe as primeiras 10 linhas com os nomes dos arquivos.

---

## 🔢 Comando `nl` (Numeração de Linhas)

- `nl arquivo.txt` → Numera todas as linhas do arquivo.
- `nl -b a arquivo.txt` → Numera todas as linhas, inclusive as em branco.
- `nl -b t arquivo.txt` → Numera apenas as linhas não em branco.
- `nl -n ln arquivo.txt` → Números alinhados à esquerda.
- `nl -n rn arquivo.txt` → Números alinhados à direita.
- `nl -n rz arquivo.txt` → Alinha à direita, preenchendo com zeros.
- `nl -s ':' arquivo.txt` → Usa o caractere ":" como delimitador.
- `nl -w 4 arquivo.txt` → Define uma largura fixa de 4 dígitos para os números.

---

## 📄 Comando `more` (Visualização Paginada Simples)

- `more arquivo.txt` → Exibe o conteúdo do arquivo de forma paginada.
- `more +5 arquivo.txt` → Inicia a exibição a partir da linha 5.
- `more -d arquivo.txt` → Exibe uma mensagem interativa (ex.: "[Press space to continue, 'q' to quit.]").
- `more -c arquivo.txt` → Limpa a tela antes de exibir a próxima página.
- `more -s arquivo.txt` → Reduz múltiplas linhas em branco adjacentes para uma única linha.

---

## 📖 Comando `less` (Visualização Paginada Avançada)

- `less arquivo.txt` → Exibe o conteúdo com navegação melhorada.
- `less +5 arquivo.txt` → Inicia a partir da linha 5.
- `less -N arquivo.txt` → Exibe números de linha.
- `less -S arquivo.txt` → Corta linhas longas (não as quebra).
- `less -X arquivo.txt` → Não limpa a tela ao sair.
- `less -i arquivo.txt` → Ignora a diferença entre maiúsculas e minúsculas durante a busca.

---

## 🔀 Comando `sort` (Ordenação de Linhas em Arquivos)

- `sort arquivo.txt` → Ordena as linhas em ordem alfabética.
- `sort -r arquivo.txt` → Ordena em ordem alfabética reversa.
- `sort -n arquivo.txt` → Ordena numericamente.
- `sort -k 2 arquivo.txt` → Ordena baseado no segundo campo.
- `sort -t: -k 3,3 arquivo.txt` → Usa ":" como delimitador e ordena pelo terceiro campo.
- `sort -u arquivo.txt` → Remove linhas duplicadas.
- `sort -o output.txt arquivo.txt` → Salva a saída ordenada em "output.txt".

---

## 🔄 Comando `|` (Pipe)

- **Função:** Redireciona a saída de um comando como entrada para outro, permitindo o encadeamento de comandos.

---

## 🔚 Comando `tail` (Exibir Final do Arquivo)

- `tail arquivo.txt` → Exibe as últimas 10 linhas (padrão).
- `tail -n 20 arquivo.txt` → Exibe as últimas 20 linhas.
- `tail -c 50 arquivo.txt` → Exibe os últimos 50 caracteres.
- `tail -f arquivo.txt` → Monitora o arquivo em tempo real (novas linhas são exibidas conforme são adicionadas).
- `tail -q arquivo1.txt arquivo2.txt` → Exibe as últimas 10 linhas de cada arquivo sem mostrar os nomes.
- `tail -v arquivo1.txt arquivo2.txt` → Exibe as últimas 10 linhas com os nomes dos arquivos.

---

## 🎛️ Atalhos e Outros Comandos

- **ALT+F2:** Muda para outro terminal.
- **`uptime`:** Exibe o tempo de atividade da máquina.

### 📟 Comando `dmesg` (Mensagens do Kernel)
- `dmesg` → Exibe todas as mensagens do buffer de anel do kernel.
- `dmesg | less` → Exibe as mensagens de forma paginada.
- `dmesg -T` → Mostra timestamps legíveis.
- `dmesg -k` → Exibe apenas mensagens do kernel.
- `dmesg -l` → Filtra mensagens por níveis de log (ex.: emergência, alerta, crítico, erro, advertência, notificação, informação).
- `dmesg -D` → Filtra mensagens por categorias (kernel, usuário, etc.).

- **MSG Y:** Ativa o modo TALK para envio de mensagens.

---

## 💬 Comando `echo` (Exibir Texto no Terminal)

- `echo "Olá, Mundo!"` → Exibe a mensagem "Olá, Mundo!".
- `echo $USER` → Exibe o nome do usuário atual.
- `echo $HOME` → Exibe o diretório home do usuário.
- `echo -n "Sem nova linha"` → Exibe o texto sem adicionar nova linha ao final.
- `echo -e "Linha1\nLinha2"` → Interpreta sequências de escape (exibe duas linhas separadas).

---

## 🔐 Comando `su` e Diferenças com `sudo`

- `su -` → Troca para o usuário root iniciando um novo shell com o ambiente do root (prática mais segura).
- `/bin/su -` → Método adequado para trocar de usuário.
- **Observação:** `sudo` pede a senha do usuário e oferece melhor auditoria; `su` pede a senha do root.

---

## 👤 Adicionar/Remover Usuários ao Grupo `sudo`

- **Adicionar um usuário ao grupo sudo:**
  - `adduser {nome-do-user} sudo`
- **Remover um usuário do grupo sudo:**
  - `deluser {nome} sudo`

---

## 💾 Comando `sync`

- `sync` → Grava os buffers do kernel no disco, garantindo que os dados sejam efetivamente escritos.

---

## 🖥️ Comando `uname` (Informações do Sistema)

- `uname -s` → Exibe o nome do kernel.
- `uname -n` → Exibe o nome do host.
- `uname -r` → Exibe a versão do kernel.
- `uname -v` → Exibe a data e hora de compilação do kernel.
- `uname -m` → Exibe a arquitetura da máquina.
- `uname -p` → Exibe o tipo de processador.
- `uname -o` → Exibe o sistema operacional.
- `uname -a` → Exibe todas as informações disponíveis.

---

## 🔄 Comando `reboot` e `shutdown`

### Reiniciar a Máquina:
- `systemctl reboot`
- `reboot`
- `reboot -f` → Força o reinício sem executar scripts de desligamento.
- `reboot -p` → Desliga o sistema ao invés de reiniciar.
- `reboot --help` → Exibe ajuda e opções.
- `echo b >/proc/sysrq/sysrz-trigger` → Executa o reboot via sysrq.

### Desligar a Máquina:
- `systemctl halt`
- `shutdown -h now` → Desliga imediatamente.
- `echo o >/proc/sysrq/sysrz-trigger` → Desliga via sysrq.
- `shutdown -h [HORÁRIO]` → Agenda o desligamento para um horário específico.
- `shutdown -h +10` → Agenda o desligamento para daqui a 10 minutos.
- `shutdown -c` → Cancela um desligamento agendado.

---

## 📝 Comando `wc` (Contar Palavras, Linhas e Bytes)

- `wc arquivo.txt` → Exibe o número de linhas, palavras e bytes do arquivo.
- `wc -l arquivo.txt` → Conta apenas as linhas.
- `wc -w arquivo.txt` → Conta apenas as palavras.
- `wc -c arquivo.txt` → Conta os bytes.
- `wc -m arquivo.txt` → Conta os caracteres.
- `wc -L arquivo.txt` → Exibe o comprimento da linha mais longa.

---

## 🔢 Comando `seq` (Gerar Sequência Numérica)

- `seq 10` → Gera uma sequência de 1 a 10.
- `seq 1 2 10` → Gera uma sequência de 1 a 10, incrementando de 2 em 2.
- `seq -w 01 1 10` → Gera a sequência com números preenchidos com zeros à esquerda.
- `seq -s ", " 1 5` → Gera uma sequência de 1 a 5, separando os números por vírgula e espaço.
- `seq -f "Número: %g" 1 3` → Gera uma sequência formatada com o prefixo "Número:".

---