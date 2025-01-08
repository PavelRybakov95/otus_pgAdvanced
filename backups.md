Создали 2 кластера
sudo pg_createcluster 16 main1 --datadir=/var/lib/postgresql/16/main
sudo pg_createcluster 16 main2 --datadir=/var/lib/postgresql/16/main2


обновили конфигурацию для второго кластера

sudo cp /etc/postgresql/16/main/postgresql.conf /etc/postgresql/16/main2/postgresql.conf
sudo cp /etc/postgresql/16/main/pg_hba.conf /etc/postgresql/16/main2/pg_hba.conf

sudo nano /etc/postgresql/16/main2/postgresql.conf

#data_directory = '/var/lib/postgresql/16/main'         # use data in another directory
data_directory = '/var/lib/postgresql/16/main2'         # use data in another directory

#port = 5432                            # (change requires restart)
port = 6432                             # (change requires restart)

sudo pg_ctlcluster 16 main2 start


echo "BACKUP_PATH=/home/backups/">>~/.bashrc
echo "export BACKUP_PATH">>~/.bashrc
cd $HOME
-- cd ~
. .bashrc

echo $BACKUP_PATH
###-!!!



#Инициализируем созданный каталог как каталог для бакапов:
pg_probackup-16 init -B /home/backups

#Перейти в каталог и посмотреть содержимое(или в любом навигаторе):
cd /home/backups
ls -l

![инициализируем оба кластера в папку с бекапом](https://github.com/user-attachments/assets/1551d1a4-8532-43d8-bdf3-7a1e923e7bb4)
Инициализировали оба кластера в указанном пути
pg_probackup-16 add-instance --instance 'main' -D /var/lib/postgresql/16/main -B /home/backups
pg_probackup-16 add-instance --instance 'main2' -D /var/lib/postgresql/16/main2 -B /home/backups

Создали базу, табличку, залили данные

Получили информацию по настройке инстанса и каталога
# Backup instance information
pgdata = /var/lib/postgresql/16/main
system-identifier = 7457522715914379693
xlog-seg-size = 16777216
# Connection parameters
pgdatabase = postgres
# Replica parameters
replica-timeout = 5min
# Archive parameters
archive-timeout = 5min
# Logging parameters
log-level-console = INFO
log-level-file = OFF
log-format-console = PLAIN
log-format-file = PLAIN
log-filename = pg_probackup.log
log-rotation-size = 0TB
log-rotation-age = 0d
# Retention parameters
retention-redundancy = 0
retention-window = 0
wal-depth = 0
# Compression parameters
compress-algorithm = none
compress-level = 1
# Remote access parameters
remote-proto = ssh

Сделали полный бекап
pg_probackup-16 backup --instance 'main' -b FULL --stream --temp-slot -B /home/backups

![Сделали полный бекап](https://github.com/user-attachments/assets/c527905c-1725-4a16-b4d1-2b0b72f49314)

Добавили значение
pg_probackup-16 show -B /home/backups
Сделали инкремент
pg_probackup-16 backup --instance 'main' -b DELTA --stream --temp-slot -B /home/backups


![Сделали инрементальный бекап](https://github.com/user-attachments/assets/ea120ead-337f-46b7-b3f5-7849fe57259c)

Останавливаем кластер2 для заливки в него бекапа

Чистим кластер
rm -rf /var/lib/postgresql/16/main2


Восстанавливаемся из FULL бэкапа у которого ИД = SPRT0B

sudo su postgres

pg_probackup-16 restore --instance 'main2' -i 'SPRT0B' -D /var/lib/postgresql/16/main2 -B /home/backups

![Успешное восстановление кластера на main2](https://github.com/user-attachments/assets/0f40f786-1561-4007-9dc4-f249865458b2)

Успешно восстановили кластер main из бекапа SPRT0B (фулл+инкремент) в кластер main2 по порту 6432
