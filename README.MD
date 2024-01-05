# Установка

Ставим с помощью python, командой 
```cmd
python -m pip install dbt-postgres
```
Проверить, что всё нормально установилось
```
dbt --version
```
Должно вернуть
```
Core:
  - installed: 1.7.4
  - latest:    1.7.4 - Up to date!

Plugins:
  - postgres: 1.7.4 - Up to date!
```
У меня ставилось с проблемами, пришлось установить:
* модули языка программирования Rust
* инсталлятор Visual Studio
* компонент C++
* обновить pip в python
* и заодно обновить setuptools и wheel

# Изучение dbt


### Инициируем dbt
Смотрел видео с YouTube:
https://www.youtube.com/watch?v=btaH7P0U_2g

Вся работа ведется в консоли
инициируем проект
```
dbt init название_проекта
```

### Берем базу postgres из бэкапа
https://www.postgresqltutorial.com/postgresql-getting-started/postgresql-sample-database/

1. Меняем кодировку консоли на "1252"
2. Создаем пустую базу с помощью "psql", команда `CREATE DATABASE dvdrental;`. Консоль должна ответить словами `CREATE DATABASE`. Если не ответила, значит ничего не сделала.
3. Переходим в файлы СУБД `cd "c:\Program Files\PostgreSQL\16\bin"`
4. Просим СУБД сделать рестор базы из архива - `pg_restore -U postgres -d dvdrental "F:\dbt-training\dvdrental.tar"`. СУБД попросит пароль от пользователя, вводим его.
5. Дальше она молча выполняет команду. Заходим, проверяем

### Настраиваем профиль для dbt

1. Идем в домашнюю директорию `~/`, ищем там папку `.dbt`
2. Скорее всего там пусто, создаем файл `profiles.yml`
3. Заполняем его по инструкции - https://docs.getdbt.com/docs/core/connect-data-platform/postgres-setup
4. Проверяем работу командой `dbt debug`
   * Получил ошибку, что не найден файл `dbt_project.yml` в корне проекта
   * Переложил его из папки `tests` в корень
   * Поменял профиль с `trainigs` на `dbt-training`. В общем, должно быть одинаково указано в `dbt_project.yml` и в `~/.dbt/profiles.yml`
   * Получаем сообщение от дебага, что все проверки пройдены

Далее пробуем запускать `dbt run`