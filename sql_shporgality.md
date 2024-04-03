![Screenshot_20240322_213244.png](..%2F..%2FPictures%2FScreenshot_20240322_213244.png)
~~~
SELECT поля_таблиц
FROM таблица_1
[INNER] | [[LEFT | RIGHT | FULL][OUTER]] JOIN таблица_2
    ON условие_соединения
[[INNER] | [[LEFT | RIGHT | FULL][OUTER]] JOIN таблица_n
    ON условие_соединения]
~~~


Говоря о многотабличном запросе со внутренним соединением общая структура выглядит так:
~~~
SELECT поля_таблиц
FROM таблица_1
[INNER] JOIN таблица_2
    ON условие_соединения
[[INNER] JOIN таблица_n
    ON условие_соединения]

~~~


