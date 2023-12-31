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

Смотрел видео с YouTube:
https://www.youtube.com/watch?v=btaH7P0U_2g

Вся работа ведется в консоли
инициируем проект
```
dbt init название_проекта
```