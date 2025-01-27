# tmdb_api
Cервис поиска рекомендуемых к просмотру фильмов.

## Описание работы составных частей программы:

### find_similar.py
Осуществляет поиск фильма в локальной бд и ранжирует их согласно рейтингу. 
Сначала запрашивает у пользователя ключевые слова для поиска, затем проверяет, входят ли эти слова в названия фильмов из бд. Затем каждому из найденых фильмов присвается
определенный рейтинг, по умолчанию пользователю показываются 8 наиболее релевантных. Используется вспомогательная функция из `own_db_helpers.py`
Для работы программы необходимо указать путь до базы данных.

Запуск поиска:
```
python find_similar.py
```
### own_db_helpers.py
Загружает базу данных фильмов. Программе надо указать путь до бд. 

### make_own_db.py
Создаёт базу данных фильмов. Используется сервис [TMDB](https://www.themoviedb.org/).
Программа загружает карточки фильмов. По умолчанию количество фильмом для загрузки  - 1000.
Результат загрузки сохраняется в файле `MyFilmDB.json`. 
Для работы скрипта используются функции из файла `tmdb_helpers.py`. Эти функции проверяют ключ к api и делают запрос к сервису TMDB.

Создать БД можно командой:
```
python make_own_db.py
```
### search_in_db.py
Скрипт осуществляет поиск фильмов в базе данных по ключевой фразе в заголовке. Для работы использует функцию  `load_data` из `own_db_helpers`.

### hello_api_TMDB.py
Вспомогательная функция для проверки доступа к api. Запрашивает у пользователя ключ и проверяет его валидность.
Если ключ валиден, то делает запрос к сервису TMDB. Возвращает бюджет фильма с id = 215.

### tmdb_helpers.py
Функции для работы с [api](https://api.themoviedb.org/) сервиса TMDB.
Позволяет безопасно ввести ключ к api, а также делать запросы к сервису. 
Запуск:
```
python tmdb_helpers.py
```
