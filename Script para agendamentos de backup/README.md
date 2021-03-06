
FAST BACKUP 
Autor: Luiz Eduardo

Sobre o fast backup 
O script fast backup foi construído para facilitar as atividades realizadas pelos utilizadores do sistema linux bem como dos administradores
que rotineiramente precisam realizar agendamentos de backup de diretórios e arquivos, o fast backup tem uma interface facilitada
não limitando o seu uso apenas para usuários avançados de sistemas linux. O fast backup conta com duas funcionalidades, geração de backup
sem agendamento e agendamento diário, semanal e mensal de backups. Os logs do fast backup ficam armazenados no diretório em que o script está. 

1.0 Como utilizar 
Antes de iniciar o script é importante lembrar que será necessário conceder permissão de execução para os usuários.
$chmod +x fastbackup.sh
para iniciar o script utilize um dos comandos abaixo 
$./fastbackup.sh 
$ . fastbackup.sh
$source fastbackup.sh


OBS: Verifique se você possui permissão para gravar alguns diretórios antes de realizar o agendamento pois caso você não possua permissãoo 
o backup não será gerado no destino informado. 


1.1 Com o script em execução 
1º Após executar o fast backup ele irá solicitar o caminho absoluto do arquivo ou diretório que você deseja gerar backup (ORIGEM) 
2º Pode ser informado quantos arquivos você quiser basta responder s|S para a a pergunta após informar a primeira origem
3º Selecione o local de destino para armazenar o backup
4º Informe uma frequência para backup  através de números 
	1-Diário
	2-Semanal
	3-Mensal
	4-Sair
Caso seja informada uma um caracter diferente dos listados acima o script apresentará uma mensagem de erro. 


1.2  Quantidade de arquivos 
Caso você não remova ou mova os arquivos/diretórios que foram bkpeados eles poderam ocupar muito espaço em disco, para amenizar esse problema
você pode estipular a quantidade de backups que deseja armazenar.


1.3 Informações de agendamento 
Os sistemas Linux possuem o cron sempre presente. Pelo menos eu nunca vi nenhuma distribuição que não incluísse o tão útil cron. A configuração tem duas partes: Uma global, e uma por usuário. Na global, que é o root quem controla, o crontab pode ser configurado para executar qualquer tarefa de qualquer lugar, como qualquer usuário. Já na parte por usuário, cada usuário tem seu próprio crontab, sendo restringido àpenas ao que o usuário pode fazer (e não tudo, como é o caso do root).

Para configurar um crontab por usuário, utiliza-se o comando crontab, junto com um parâmetro, dependendo do que você quiser fazer. Abaixo uma relação:

Comando	Função
crontab -e	Edita o crontab atual do usuário
crontab -l	Exibe o atual conteúdo do crontab do usuário
crontab -r	Remove o crontab do usuário
Se você quiser verificar os arquivos crontab dos usuários, você precisará ser root. O comando crontab coloca os arquivos dos usuários no diretório:

/var/spool/cron/usuario
Onde “usuario” corresponde ao usuário dono do arquivo crontab.

Agora se você quiser editar o crontab global, este fica no arquivo “/etc/crontab“, e só pode ser manipulado pelo root. E agora que já sabemos onde ficam os arquivos de configuração, vamos estudar o formato da linha do crontab, que é quem vai dizer o que executar e quando. Vamos ver um exemplo:

0  4  *  *  *  who
Então como se pode ver, a linha é dividida em 6 campos separados por tabs ou espaço:

Campo	Função
1o.	Minuto
2o.	Hora
3o.	Dia do mês
4o.	Mês
5o.	Dia da semana
6o.	Programa para execução
Todos estes campos, sem contar com o 6o., são especificados por números. Veja a tabela abaixo para os valores destes campos:

Campo	Valores
Minuto	0-59
Hora	0-23
Dia do mês	1-31
Mês	1-12
Dia da semana	0-6 (o “0″ é domingo), 1 é segunda, etc.

	   
1.4 LOG 
LOGS de execução 
Toda vez que o fast-backup.sh for executado será gerado um arquivo de log no diretório que ele foi executado na pasta /logs/Agendamentos.log  
Informações gravadas no arquivo de LOG local 
	-Hora de execução do script
	-Nome do usuário que está logado
	-Diretório que foi executado o script 
LOGS de backup 
Os logs de backup serão armazenados em outro diretório $HOME/fast-backup/fast-backup.log 
Informações gravadas no arquivo de LOG de backup 
	-Inicio de execução do backup 
	-Diretório origem
	-Diretório destino
	-Data de execução 
