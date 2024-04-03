## Python Advanced
# Template of flask app
~~~
from flask import Flask, request

app = Flask(__name__)


@app.route("/registration", methods=["POST"])
def registration():
    form_data = request.get_data(as_text=True)
    print(f"{form_data = }")
    return "ОК"


if __name__ == "__main__":
    app.run(debug=True)
~~~

###  lesson 1

~~~
    app.config["WTF_CSRF_ENABLED"] = False
~~~
- example of data form post CURL request
~~~
curl -X POST http://127.0.0.1:5000/divide/ --data "a=5&b=1"
~~~
-example to send JSON arrey of numbers
~~~
curl -X POST -H "Content-Type: application/json" -d '[1, 5, 3, 2, 4]'
~~~
- python3 -m venv .venv
- source ./.venv/bin/activate
- pip freeze - Для получения всех установленных библиотек в этом окружении
- pip freeze > requirements.txt в файл отправить зависимости
- pip install -r requirements.txt - установка зависимостей из файла
- pip uninstall flask

### команды лектора по запуску проекта
- export FLASK_APP="app.py"
- export FLASK_DEBUG=1
- python -m flask run --port=5555

### lesson 2

- **Конвейер (pipe)** — это механизм передачи данных со стандартного потока вывода одной программы на стандартный поток ввода другой программы. Пример запуска конвейера:

    ```
    $ ls -R | grep "\.txt" | wc -w
      1)      2)             3)
    ```

    1) Получаем рекурсивно все файлы в текущем каталоге.
    2) Получаем из них файлы с расширением .txt.
    3) Получаем общее количество слов в .txt-файлах.

- Получить входные данные можно следующим образом:

    ```python
    import sys
    
    data = sys.stdin.read()
    ```
    Вывод можно делать с помощью того же print.

- Входные данные можно получить сразу в виде списка строк:

    ```python
    lines = sys.stdin.readlines()
    ```

- Первая строка не является информацией о файле, поэтому её можно отбросить при прочтении входных данных:

    ```python
    lines = sys.stdin.readlines()[1:]
    ```

- Кстати, программа также может получать информацию из файла и из результата выполнения другой команды или программы.

    ```
    $ ls -l > ls.txt
    $ python3 get_mean_size.py < ls.txt
    $ cat ls.txt | python3 get_mean_size.py
    ```
    
    `cat <filename>` выводит содержимое файла.


### взять день недели/ посмотреть размер объекта
  ~~~
  from datetime import datetime
  weekday = datetime.today().weekday()'
  ~~~

```python
import sys
print(sys.getsizeof(weekdays_tuple))
```

### выводит значение из словарь если, значения нет создается ключ значение

~~~
any = dict()
any.setdefault('1989', {}).setdefault('май', {}).setdefault('25', 2)
2
~~~


### регулярка выводит числа из пути ендпоинта убирая слешы, и проверяя корректность

~~~
/лордлор5454/54/--854/1,2/8/6/98
pattern = r'(?:^|/)(\d+)(?=/|$)'
numbers = re.findall(pattern, path)
54,8,6,98

~~~

## Lesson 3


- my date from query checker: 
~~~
pattern = r'^(?P<year>(?:19|20)\d{2})(?P<month>[01][0-9])(?P<day>[0-3][0-9])$'
match = re.match(pattern, date)
if match:
    year = int(match.group('year'))
    month = int(match.group('month'))
    day = int(match.group('day'))
else:
    return "Pattern not found. Date format: YYYYMMDD<br>example: 19000101 to 20991231"
~~~

## lesson 4

- Отправка GET-запроса:
~~~
curl <URL>
~~~
- Отправка GET-запроса с параметрами:
~~~
curl "<URL>?param1=value1&param2=value2"
~~~
- Отправка POST-запроса с данными в теле запроса:
~~~
curl -d "data" <URL>
~~~
- Отправка POST-запроса с данными в теле запроса в формате JSON:
~~~
curl -H "Content-Type: application/json" -d '{"key": "value"}' <URL>
~~~

### install Flask WTF
~~~
pip install Flask-WTF
~~~