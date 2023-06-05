# CronTab

Crontab é um arquivo de configuração utilizado para scheduler tarefas no sistema Linux. O Crontab contém uma lista de linhas, que representam diversas tarefas agendadas. Cada linha contém o horário e a data em que a tarefa será executada, seguida do comando ou script que será executado. O Crontab é uma ferramenta muito útil para automatizar tarefas repetitivas, como backups, atualizações de software, entre outros. É importante ter cuidado ao configurar o Crontab, garantindo que as tarefas agendadas não interfiram no desempenho do sistema ou em outras tarefas agendadas.

1 - Logar como root 
```bash
felipe@notebook-550XDA:~$ sudo su
```

2 - Abrir crontab
```bash
root@notebook-550XDA:/etc# nano /etc/crontab 
```

3 - Definir  o horário da execução e o caminho  do script
```bash
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# Example of job definition:
# .---------------- minute (0 - 59)
# |  .------------- hour (0 - 23)
# |  |  .---------- day of month (1 - 31)
# |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ...
# |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7) OR sun,mon,tue,wed,thu,fri,sat
# |  |  |  |  |
# *  *  *  *  * user-name command to be executed
17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
54 21   * * *   root    ./home/felipe/Documentos/script.sh
#

```