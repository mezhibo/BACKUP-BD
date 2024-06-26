**Задание 1. Резервное копирование**

*Кейс*

Финансовая компания решила увеличить надёжность работы баз данных и их резервного копирования.

Необходимо описать, какие варианты резервного копирования подходят в случаях:

1.1. Необходимо восстанавливать данные в полном объёме за предыдущий день.

1.2. Необходимо восстанавливать данные за час до предполагаемой поломки.


**Решение 1**

*1.1. Необходимо восстанавливать данные в полном объеме за предыдущий день:*

- Полное резервное копирование (Full Backup): это метод предполагает копирование всех данных и баз данных в целом. При использовании этого метода восстановление за предыдущий день будет возможно, но требуется больше места для хранения резервной копии и времени на ее создание.

- Инкрементное резервное копирование (Incremental Backup): сначала создается полная копия базы данных, а затем в последующие дни создаются инкрементные копии, в которых сохраняются только измененные данные с момента предыдущего копирования. Этот метод экономит место на диске, но требует восстановления последовательности копий для полного восстановления данных.

*1.2. Необходимо восстанавливать данные за час до предполагаемой поломки:*

- Транзакционное журналирование (Transaction Log Backup): данный метод позволяет сохранять все транзакции, произошедшие с момента последнего резервного копирования транзакционного журнала. Это позволяет восстановить данные до момента сбоя, вплоть до часа до него, сохраняя целостность транзакций.
  
- Моментальное резервное копирование (Instant Backup): этот метод позволяет создавать мгновенные снимки баз данных, что позволяет восстановить данные до момента создания снимка. Он обеспечивает более быстрое восстановление данных в случае аварии или сбоя.



**Задание 2. PostgreSQL**

*2.1. С помощью официальной документации приведите пример команды резервирования данных и восстановления БД (pgdump/pgrestore).*

**Решение 2**

*2.1 Пример создания резервной копии базы данных с сохранением структуры и данных:*

pg_dump -U username -d testdatabase -f backup.sql


*Пример резервного восстановления из базы данных:*

pg_restore -U username -d testdatabase backup.sql



**Задание 3. MySQL**

*3.1. С помощью официальной документации приведите пример команды инкрементного резервного копирования базы данных MySQL.*


**Решение 3**

*3.1.Пример комманды инкрементного резервного копирования базы данных MySQL*

mysqldump --user=admin --password=12345 --single-transaction --quick --lock-tables=false testdatabase > incremental_backup.sql
