# Anotações Linux

 PREFÁCIO

- Fundamentos do Shell e Comandos Básicos [ir para o dia 02](#day-02)
- Comandos Avançados e Comandos Internos/Externos[ir para o dia 03](#day-03)






<a id="day-02"></a>

# **DAY 2**


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

# DAY-3:COMANDOS INTERNOS E EXTERNOS NO LINUX


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


