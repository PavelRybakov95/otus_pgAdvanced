Создаем кластер постгрес через Managed Service for PostgreSQL. указываем необходимые параметры

![создание кластера1](https://github.com/user-attachments/assets/de58adfb-f344-4f1f-8fda-d5c8ffd6cd6a)
![создание кластера2](https://github.com/user-attachments/assets/cae4ab0d-d886-4ee9-9777-205939c5329e)

После создания кластера добавляем подключение через Yandex MetaData Hub
Подключаемся.

![создание подключения к постгресу](https://github.com/user-attachments/assets/714afbef-f4ed-4d71-ba91-bc94900d114c)
[подключились из hub](https://github.com/user-attachments/assets/77a77691-1546-4a3f-956b-007fc44b78f0)

После пришлось немного помучаться. Для подключения о своего компа, как оказало, нужно разрешить удаленные подключения по имени к кластеру (отдельной машине). 
Но в конечном счете все получилось.

![добавление возможности всех подключений](https://github.com/user-attachments/assets/271aba2a-c5c5-4d03-914d-0dc3be592e10)
![подключились с личного ПК через Бобра](https://github.com/user-attachments/assets/88dd1d0b-a3c2-4edd-b7b0-12392679dca7)
