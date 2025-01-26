Создали ВМ в ЯО, добавили подключение через бобра (не знаю зачем..)
![параметры машины](https://github.com/user-attachments/assets/8f56d761-cb27-4fbb-b94a-4f57cc4d0688)

![создали](https://github.com/user-attachments/assets/56229186-0bee-4b58-b082-4409ee984440)

Подготовили базу postgres для выполнения тестов pg_bench \c postgres pgbench -i

![Подготовили базу postgres для pg_bench](https://github.com/user-attachments/assets/4dd5468e-05d8-4315-913f-282fea6afccf)

1. Выполнили тесты на "дефолтной машине"
2. Выполнили тесты сконфигурировав postgres с помощью https://www.pgconfig.org/ указано 4 гб памяти
3. Выполнили тесты сконфигурировав postgres с помощью https://www.pgconfig.org/ указано 2 гб памяти
4. 
Результаты тестов предоставлены ниже:

![таблица результатов](https://github.com/user-attachments/assets/f8f6743a-4e23-494f-b374-6537360f26d3)

Количество транзакций +10%, tps (transaction per second) - цифра плавающая, время пераого подключения возрасло с применением новых настроек, latency снизилась примерно на 20%

В первом случае тюнинга указал параметры 4 Гб памяти, второй тест 2Гб памяти, влияние на производительность в рамках теста несущественное.

Файл конфигураций прикладываю

[заметочки.txt](https://github.com/user-attachments/files/18551243/default.txt)
