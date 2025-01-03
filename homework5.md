Создали машинку в ЯО

![создаем виртуалку1](https://github.com/user-attachments/assets/e452742e-069e-4ae9-af8b-60b40d5cda32)
![создаем виртуалку2](https://github.com/user-attachments/assets/4f232c51-40fd-425e-9d35-c7ce13fd8ff1)
![создаем виртуалку3](https://github.com/user-attachments/assets/5c6a08b5-3c83-4902-b6b2-7f9450174603)

Установили постгрес, создали табличку, добавли тестовую строку.
![проверка доступности кластера](https://github.com/user-attachments/assets/1a2c1710-d953-4895-afc8-9b70d56e74f2)

Остановили постгрес, добавили, смониторвали диск по инструкции: https://support.ncomputing.com/portal/en/kb/articles/how-to-partition-and-format-storage-devices-in-linux инструкцция приложенная к уроку, к сожалению не открылась =(

![добавляем диск](https://github.com/user-attachments/assets/a9c26593-d8f1-4ce1-ad82-e2b26c686407)
![смонтировали диск, перенесли ПГ](https://github.com/user-attachments/assets/592b1c8a-ac1e-43ef-8926-e0a5ce30e64f)

Попытались запустить постгрес - не вышло, так как дата дирректория перенесена. Сменили путь к \data и постгрес завелся.

![сменили путь дата дирректории](https://github.com/user-attachments/assets/81e85b85-4ce7-4570-9840-46f3213b87e3)

После смены дирректория постгрес завелся, данные в тестовой табличке сохранились. Как будто успех

![после смены кофигурации класте завелся, данные в табличке сохранились](https://github.com/user-attachments/assets/20193952-cc15-4d4f-af27-2e312559412b)
