##Все манипуляции на хостах выполнялись через SSH, мне показался этот вариант более приближенный к тому, с чем предстоит работать.

Создали 7 одинаковых виртуалок в ЯК

![создание вм2](https://github.com/user-attachments/assets/dbeae7bd-6129-4492-b10b-8adfa43f3dfd)
![создание ВМ1](https://github.com/user-attachments/assets/aabee51a-0ff2-4f13-a237-f03a6a811f5c)
![редактируем подсеть](https://github.com/user-attachments/assets/ebb91429-54d9-4d04-adf2-a31cf37def61)
![создаем сеть](https://github.com/user-attachments/assets/c2964f0c-b410-4f59-9605-72e6b8643922)

На всех 7 машинах прописываем хосты в файлки /etc/hosts
![на всех машинах в hosts прописываем ip](https://github.com/user-attachments/assets/5fb743bb-b7cf-4c5a-819c-71557ae15402)

На 3 нодах etcd установили и настроили etcd, не с первого раза, к сожалению. Нет пактов для ubuntu 24.04 (в файлике новый5.txt описаны шаги как ставил ну и вся последовательность действий.)

![члены etcd ](https://github.com/user-attachments/assets/c8abaf4b-7d4f-4bbd-b699-22643c3314a0)

Установили postgres, патрони, сконфигурировали (все в файлике новый5.txt)
Кластер собрали, видимо успешно =)

![кластер патрони](https://github.com/user-attachments/assets/af1b302d-f62c-47ea-a363-768d69fe3d1b)

Установили haproxy

Имитируем сбой, собственно выключаем патрони на ноде (1), видим что переезд случился на вторую ноду, возвращаем к жизни первую ноду патрони и все в порядке.

![остановили патрони на 1 ноде](https://github.com/user-attachments/assets/2625bb54-8be7-4729-a444-3f794f73a020)

![на ноде 2 видим переезд](https://github.com/user-attachments/assets/b33b57df-059d-4265-8c20-aca16a963234)

![статус после переезда](https://github.com/user-attachments/assets/337b9ccb-969d-439c-b52a-990ebc6b1ecd)

Добавляем данные на первичной ноде. Проверяем, что на вторичной ноде есть изменения внесенные на перивичной ноде

![вывод данных со вторичной реплики](https://github.com/user-attachments/assets/2baddab0-cd41-4f2b-ad09-b46644445cd0)

Ну и попробовал установить pg_probackup или wal-g и снова траблы.. скачать не удалось

![настройка бекапов не удалась](https://github.com/user-attachments/assets/d762ec5b-6fa4-4cde-880d-8c82ca261529)
