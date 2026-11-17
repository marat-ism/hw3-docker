## Шаблон для третьего ДЗ по ИПР

Условие дз доступно по [ссылке](https://github.com/Nikfilk2030/missing_semester_hse_cs/blob/main/2026/amcs/year_1/hw_3/README.md)

## Задания на 6 баллов

Команда запуска: 'docker compose up -d --build'

Сначала счетчик был 0, затем я сделал команду 'curl -X POST http://127.0.0.1:8080/increment' и счетик увеличился на 1 и стал равен 1 и hostname стал равен c73d09117675

Потом я сделал команды 'docker compose down', 'docker compose up -d', 'curl http://127.0.0.1:8080/'

После этих команд контейнер пересоздался и счетчик остался равным 1 и hostname стал f87a22007ce7

Данные сохранились в volume counter_data, который подключен к /data и я не использовал флаг -v

## Задания на 8 баллов

Приложения запускается по 'docker compose up -d --build', команда 'docker compose ps' показала healthy у app и redis

После того, как я сделал 4 запроса 'curl -X POST http://127.0.0.1:8080/increment' счетчик стал равен 4

Я выполнил команды 'docker compose down', 'docker compose up -d', 'curl http://127.0.0.1:8080/', счетчик не изменился и равен 4, а hostname изменился с 6efce78b54c7 на ae12b1b5b9b2, а также я не использовал флаг -v, как было рекомендовано в задании

После того, как я написал 'docker compose stop redis', я сделал команды: 'curl -i http://127.0.0.1:8080/healthz', 'curl -i http://127.0.0.1:8080/readyz', 'curl -i -X POST http://127.0.0.1:8080/increment' - показали 200, 503, 503 соответственно, это хорошо, как раз то, что написано в задании.

Затем я выполнил команду 'docker compose start redis', потом 'curl -i http://127.0.0.1:8080/readyz' - вернул 200, то есть он работает, потом после команды 'curl http://127.0.0.1:8080/' счетчик покаал 4, а после команды 'curl -X POST http://127.0.0.1:8080/increment' счетчик стал равен 5 и hostname остался ae12b1b5b9b2 и вручную приложение я не перезапускал

## Запуск приложения

Я писал все команды из корневой папки, перед первым запуском надо скопировать '.env.example' в '.env' APP_PORT(=8080 по умолчанию)-порт компьютера и GREETING-приветствие

Команда запуска 'docker compose up -d --build', состояние 'docker compose ps', логи 'docker compose logs', остановка c cохранением данных 'docker compose down'

Приложение находиться по адресу http://127.0.0.1:8080/ или на порту из APP_PORT

В compose.yaml работа app и redis, данные сохраняются в volume redis_data

Логи задания на 4 балла в logs.txt