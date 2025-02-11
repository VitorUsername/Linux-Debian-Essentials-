# Anotações Linux

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

# **DAY 3**

(*continuar as anotações aqui*)
