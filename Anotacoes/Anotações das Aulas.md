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
Essas foram as anotações do Dia 2 do curso de Linux Admin. Caso precise de mais informações ou queira complementar algo, sinta-se à vontade para editar!

