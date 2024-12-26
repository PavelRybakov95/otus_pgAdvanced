Создали ВМ, сгенирировали ключ SSH, пробросили ключ на локальный комп.
Поключились к ВМ с локального ПК
![СозданиеВМ1](https://github.com/user-attachments/assets/b8ec91df-44bc-4f23-a3fb-d6d7c5177871)
![СозданиеВМ2](https://github.com/user-attachments/assets/b5c2c635-78e1-4c20-bddb-36a201a8cc0d)
![ВМ1](https://github.com/user-attachments/assets/8482ac4e-e859-4e3d-a412-9596e8591834)
Меняем пароль для postgres. Применяем настройки конфигурации и pg_hba
![pg1](https://github.com/user-attachments/assets/1c0c954c-a1c6-4f5a-97c2-8cc16e759131)
![pg2](https://github.com/user-attachments/assets/b5904b08-5074-4198-bf09-55f1834401d7)

Создаём базу, таблицу. Отключаем автокоммит. Запускаем первый тест\
![afetrchngeparameters](https://github.com/user-attachments/assets/c9d89d29-d1e1-4033-acee-3be8f881f9af)
![izolationlavel](https://github.com/user-attachments/assets/89850a13-a517-403c-926d-4eb17190689b)
Уровень изоляции read commited не допускает грязное чтение. После коммита всё ок.\
Запускаем второй тест\
Тоже самое. repetable read не допускает грязное чтение.\

