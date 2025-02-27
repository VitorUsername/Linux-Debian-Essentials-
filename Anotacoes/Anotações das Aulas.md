## ÍNDICE DAS AULAS
- [DAY 02](#day-02)
- [DAY 03](#day-03)
- [DAY 04](#day-04)

<a id="day-02"></a>

## Anotações - Curso Linux Admin (Dia 2)

### Comandos

- `cat` - Exibe o conteúdo de arquivos.
- `pwd` - Mostra o diretório atual.
- `history` - Exibe o histórico de comandos utilizados.
- `su -` - Alterna para o superusuário (root).
- `cd` - Navega entre diretórios.
  - `cd ~` - Retorna ao diretório home.
  - `cd -` - Retorna ao diretório anterior.
  - `cd ..` - Sobe um nível no diretório.
  - `cd /` - Vai para o diretório raiz.
- `ls` - Lista arquivos e diretórios.
  - `ls -a` - Lista todos os arquivos, incluindo ocultos.
  - `ls -al` - Exibe detalhes dos arquivos, como permissões e proprietário.
  - `ls -lha` - Exibe tamanhos de arquivos em formato legível.
- `| grep` - Filtra saída de comandos.
- `| more` e `| less` - Paginação de saída de comandos.
- `df -h` - Mostra espaço em disco.
- `echo "texto" > arquivo` - Escreve dentro de um arquivo.
- `halt`, `reboot`, `shutdown` - Comandos para desligar e reiniciar o sistema.
  - `shutdown -h now` - Desliga imediatamente.
  - `shutdown -r now` - Reinicia imediatamente.
  - `shutdown -h 20:00` - Agenda desligamento às 20h.
  - `shutdown -c "Mensagem"` - Cancela um desligamento agendado.

### Navegação e Atalhos

- `CTRL + L` - Limpa a tela.
- `CTRL + D` - Sai do terminal.
- `TAB` - Auto completa comandos e diretórios.
- `SHIFT + PGUP / PGDN` - Rola a tela para cima ou para baixo.

### Estrutura de Diretórios no Linux

- `/bin` - Contém binários essenciais.
- `/sbin` - Contém binários administrativos.
- `/boot` - Arquivos essenciais para inicialização.
- `/dev` - Arquivos de dispositivos do sistema.
- `/etc` - Arquivos de configuração do sistema.
- `/home` - Diretórios pessoais dos usuários.
- `/root` - Diretório home do superusuário.
- `/lib` - Bibliotecas compartilhadas do sistema.
- `/mnt` - Ponto de montagem temporário.
- `/opt` - Pacotes de software opcionais.
- `/proc` - Informações sobre processos e kernel.
- `/tmp` - Arquivos temporários.
- `/usr` - Recursos do sistema compartilhados.
- `/var` - Dados variáveis como logs e emails.

### Particionamento

- `sda` - Primeiro disco.
- `sda1` - Primeira partição do primeiro disco.
- `sdb` - Segundo disco.
- `sdc` - Terceiro disco.
- Partições podem ser primárias (até 4) ou lógicas.

### Shells e Troca de Shell

- O Debian usa o shell `bash` por padrão.
- Para listar os shells disponíveis: `cat /etc/shells`.
- Para mudar de shell, basta digitar o nome do shell desejado.

---
<a id="day-03"></a>

# Comandos Aprendidos Day-03


## Comandos Internos
Comandos internos, também chamados de **Built-In Commands**, são comandos imbutidos no próprio shell. Eles são carregados na memória assim que o shell inicia e não precisam de arquivos externos para serem executados.

### Exemplos de Comandos Internos:
- `cd` → Muda o diretório atual.
- `echo` → Exibe texto no terminal.
- `pwd` → Mostra o diretório atual.
- `export` → Define variáveis de ambiente.
- `alias` → Cria atalhos para comandos.
- `exit` → Fecha o terminal.

Os comandos internos são mais rápidos que os comandos externos, pois são carregados na memória assim que o shell inicia.

## Comandos Externos
Comandos externos são programas armazenados no sistema de arquivos e executados pelo shell. Para funcionar, o sistema precisa localizar o binário correspondente no `PATH` e carregá-lo na memória.

### Exemplos de Comandos Externos:
- `ls` → Lista arquivos e diretórios.
- `cat` → Exibe o conteúdo de arquivos.
- `grep` → Filtra texto com base em padrões.
- `find` → Busca arquivos no sistema.
- `tar` → Compacta e descompacta arquivos.
- `nano` → Editor de texto no terminal.

Comandos externos são mais flexíveis e podem ser substituídos ou atualizados sem alterar o shell.

## Como saber se um comando é interno ou externo?

### Exemplos de comandos para usar:
- `type cd` → Exemplo de comando interno.
- `type ls` → Exemplo de comando externo.

Use o comando `which` para verificar se um comando tem um binário associado (se tiver, é externo):
- `which ls` → Retorna `/bin/ls` (é externo).
- `which cd` → Não retorna nada (é interno).

## PATH
A variável `PATH` é usada pelo shell para determinar os diretórios nos quais procurar por comandos executáveis. Quando você digita um comando no terminal, o shell verifica primeiro se é um comando interno. Se não for, ele então procura nos diretórios listados na variável `PATH`.

### Como usar:
- `echo $PATH` → Imprime os diretórios onde o shell procura pelos binários.

A saída será algo assim:
`/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin`

## Comandos Aprendidos Day-03

- `echo` → Exibe um texto no terminal.
- `$PATH` → Variável de diretórios onde o shell verifica onde o binário estará.
- `echo $PATH` → Imprime os diretórios onde o shell procura os binários.
- `alias` → Cria atalhos para comandos.
- `which <comando>` → Serve para encontrar o binário do comando. Se o `which` não localizar, o comando é interno.
- `type` → Informa se o comando é interno ou externo.

---

# Comandos para Manipulação de Diretórios

## Comandos para abrir arquivos:
- `cat <arquivo>` → Exibe o conteúdo de um arquivo.
- `cat <diretório/arquivo>` → Exibe o conteúdo de um arquivo em um diretório específico.

## Comandos para escrever em arquivos:
- `echo <texto> > <arquivo>` → Escreve o texto no arquivo.
- `echo <texto> > <diretório/arquivo>` → Escreve o texto no arquivo dentro de um diretório específico.

## Comandos para criar arquivos:
- `touch <arquivo>` → Cria um arquivo.
- `touch .<arquivo>` → Cria um arquivo oculto.
- `touch <arquivo>~` → Cria um arquivo de backup.
- `touch <diretório>/` → Cria um diretório.
- `touch <diretório>*` → Cria um arquivo executável.

## Comandos para criar pastas:
- `mkdir <pasta>` → Cria uma pasta.
- `mkdir -p <diretório1/diretório2/diretório-final>` → Cria múltiplos diretórios.

## Comandos `ls`
- `ls` → Lista arquivos e diretórios.
- `ls -a` → Lista arquivos e diretórios ocultos.
- `ls -B` → Lista todos, menos arquivos de backup.
- `ls -A` → Exibe tudo, menos os diretórios `.` e `..`.
- `ls -a --color` → Lista com cores.
- `ls -A <diretório>` → Lista o conteúdo de um diretório específico.
- `ls -d <diretório>` → Lista apenas diretórios.
- `ls -l <diretório>` → Exibe detalhes dos arquivos.
- `ls -f` → Classifica por ordem de criação e alteração dos diretórios.
- `ls -F` → Classifica e separa diretórios, arquivos de backup, ocultos, etc.
- `ls -G` → Oculta a coluna do grupo.
- `ls -n` → Exibe informações numéricas.
- `ls -L` → Exibe o link alvo (se houver).
- `ls -o` → Exibe apenas os donos dos arquivos.
- `ls -t` → Lista arquivos por data de modificação.
- `ls -r` → Reverte a ordem de listagem.
- `ls -latr` → Exibe os logs alterados por último.

## Comando `tree`
- `tree` → Exibe a árvore de diretórios.
- `tree -A` → Usa os parâmetros do `ls` com o comando `tree`.

## Comando `rmdir`
- `rmdir` → Remove diretórios vazios.
- `rmdir -p` → Remove toda a estrutura de diretórios, se estiver vazia.

## Comandos para listar conteúdo de várias pastas:
- `ls -A <pasta1> <pasta2>` → Lista os arquivos de várias pastas.
- `ls -A <pasta1/arquivo> <pasta2>` → Lista arquivos específicos de diferentes pastas.

---

# Comandos para Manipulação de Arquivos

## Comando `cat`
- `cat -n` → Exibe o conteúdo do arquivo com números nas linhas.
- `cat -s` → Oculte linhas em branco repetidas.
- `cat -b` → Numera apenas as linhas com conteúdo.
- `cat -e` → Adiciona `$` ao final de cada linha.
- `cat -T` → Exibe caracteres de controle (como tabulação).

### Visualização de Arquivos Compactados:
- `zcat <arquivo.gz>` → Exibe conteúdo de arquivos `.gz`.
- `bzcat <arquivo.bz>` → Exibe conteúdo de arquivos `.bz`.
- `xzcat <arquivo.xz>` → Exibe conteúdo de arquivos `.xz`.

## Comando `rm`
- `rm <arquivo>` → Remove um arquivo.
- `rm -r <diretório>` → Remove um diretório.
- `rm -rf <diretório>` → Remove diretórios sem confirmação.
- `rm -i` → Pergunta antes de remover.
- `rm -f` → Força a remoção.
- `rm -rf *` → Remove todos os arquivos não ocultos.
- `rm -- -` → Remove arquivos que começam com `-`.
- `rm -f <letra>*` → Remove arquivos que começam com a letra especificada.
- `rm -rf <diretório/*>` → Remove todos os conteúdos de uma pasta.

## Comando `cp`
- `cp <origem> <destino>` → Copia arquivos ou diretórios.
- `cp -r <origem> <destino>` → Copia diretórios recursivamente.
- `cp -vfr` → Copia arquivos com exibição detalhada.
- `cp -R` → Copia dispositivos especiais.
- `cp -vs` → Copia com arquivos simbólicos.
- `cp -u` → Copia arquivos atualizados.
- `cp -x` → Não copia arquivos dentro de pastas de mesma estrutura.
- `cp -a` → Copia recursivamente preservando atributos.

## Comando `mv`
- `mv <arquivo1> <novo_nome>` → Renomeia ou move arquivos.
- `mv <diretório/aula> .` → Move arquivos para o diretório atual.
- `mv <arquivo> <diretório>` → Move um arquivo para o diretório especificado.

---

# Editores de Arquivos
- `nano` → Editor de texto simples no terminal.
- `vim` → Editor de texto avançado no terminal.
- `mcdit` → Editor de texto no terminal.

---
<a id="day-04"></a>
# Lista de Comandos Aprendidos - Aula Dia 04

## Curingas e Caracteres Especiais
- `*` → Representa nenhum, um ou mais caracteres.
- `?` → Representa um único caractere.
- `[]` → Define uma referência de caracteres.
- `{}` → Especifica padrões de strings.

## Comandos Diversos
- `clear` / `CTRL+L` → Limpar a tela.
- `#` → Comentário.

## Comando `date`
- `date`
- `date -s "08:30"`
- `hwclock --systohc`
- `date +%d-%m-%Y`
- `date +%T`

## Comando `df`
- `df`
- `df -h`
- `df -H`
- `df -l`
- `df -m`
- `df -a`
- `df -i`
- `df -T`
- `df -t`

## Comando `ln`
- `ln /bin/ls ls1`
- `ln -s /usr/bin link-do-ls`
- `cp -rvl /usr /tmp/usr-link`

## Comando `du`
- `du -H`
- `du -h`
- `du -s`
- `du -k`
- `du -m`
- `du --inodes -s`

## Comando `find`
- `find /caminho -name "arquivo.txt"`
- `find /caminho -iname "arquivo.txt"`
- `find /caminho -type f`
- `find /caminho -type d`
- `find /caminho -size +10M`
- `find /caminho -user nome_usuario`
- `find /caminho -group nome_grupo`
- `find /caminho -perm 755`
- `find /caminho -mtime -7`
- `find /caminho -atime +30`
- `find /caminho -ctime -1`
- `find /caminho -name "*.bak" -delete`
- `find /caminho -maxdepth 2 -name "*.txt"`
- `find /caminho -mindepth 2 -name "*.txt"`

## Comando `free`
- `free -h`
- `free -b, -k, -m, -g`
- `free -s 5`
- `free -t`
- `free -c 3`

## Comando `grep`
- `grep -i "padrão" arquivo.txt`
- `grep -v "padrão" arquivo.txt`
- `grep -r "padrão" /caminho`
- `grep -l "padrão" *.txt`
- `grep -n "padrão" arquivo.txt`
- `grep -c "padrão" arquivo.txt`
- `grep -A 3 "padrão" arquivo.txt`
- `grep -B 3 "padrão" arquivo.txt`
- `grep -C 3 "padrão" arquivo.txt`

## Comando `head`
- `head -n 5 arquivo.txt`
- `head -c 20 arquivo.txt`
- `head -q arquivo1.txt arquivo2.txt`
- `head -v arquivo1.txt arquivo2.txt`

## Comando `nl`
- `nl arquivo.txt`
- `nl -b a arquivo.txt`
- `nl -b t arquivo.txt`
- `nl -n ln arquivo.txt`
- `nl -n rn arquivo.txt`
- `nl -n rz arquivo.txt`
- `nl -s ':' arquivo.txt`
- `nl -w 4 arquivo.txt`

## Comando `more`
- `more arquivo.txt`
- `more +5 arquivo.txt`
- `more -d arquivo.txt`
- `more -c arquivo.txt`
- `more -s arquivo.txt`

## Comando `less`
- `less arquivo.txt`
- `less +5 arquivo.txt`
- `less -N arquivo.txt`
- `less -S arquivo.txt`
- `less -X arquivo.txt`
- `less -i arquivo.txt`

## Comando `sort`
- `sort arquivo.txt`
- `sort -r arquivo.txt`
- `sort -n arquivo.txt`
- `sort -k 2 arquivo.txt`
- `sort -t: -k 3,3 arquivo.txt`
- `sort -u arquivo.txt`
- `sort -o output.txt arquivo.txt`

## Comando `tail`
- `tail arquivo.txt`
- `tail -n 20 arquivo.txt`
- `tail -c 50 arquivo.txt`
- `tail -f arquivo.txt`
- `tail -q arquivo1.txt arquivo2.txt`
- `tail -v arquivo1.txt arquivo2.txt`

## Comando `uptime`
- `uptime`

## Comando `dmesg`
- `dmesg`
- `dmesg | less`
- `dmesg -T`
- `dmesg -k`
- `dmesg -l`
- `dmesg -D`

## Comando `echo`
- `echo "Olá, Mundo!"`
- `echo $USER`
- `echo $HOME`
- `echo -n "Sem nova linha"`
- `echo -e "Linha1\nLinha2"`

## Comando `su` e `sudo`
- `su -`
- `/bin/su -`
- `adduser nome-do-user sudo`
- `deluser nome sudo`

## Comando `sync`
- `sync`

## Comando `uname`
- `uname -s`
- `uname -n`
- `uname -r`
- `uname -v`
- `uname -m`
- `uname -p`
- `uname -o`
- `uname -a`

## Comando `reboot`
- `systemctl reboot`
- `reboot`
- `reboot -f`
- `reboot -p`
- `reboot --help`
- `echo b >/proc/sysrq-trigger`
- `systemctl halt`
- `shutdown -h now`
- `shutdown -h [HORÁRIO]`
- `shutdown -h +10`
- `shutdown -c`

## Comando `wc`
- `wc arquivo.txt`
- `wc -l arquivo.txt`
- `wc -w arquivo.txt`
- `wc -c arquivo.txt`
- `wc -m arquivo.txt`
- `wc -L arquivo.txt`

## Comando `seq`
- `seq 10`
- `seq 1 2 10`
- `seq -w 01 1 10`
- `seq -s ", " 1 5`
- `seq -f "Número: %g" 1 3`

