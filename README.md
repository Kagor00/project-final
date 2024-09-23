## Підсумковий проєкт 5-го модуля JavaRush
## Виконавець: Колибаба Ігор Володимирович

## [REST API](http://localhost:8080/doc)

## Концепція:

- Spring Modulith
    - [Spring Modulith: чи досягли ми зрілості модульності](https://habr.com/ua/post/701984/)
    - [Introducing Spring Modulith](https://spring.io/blog/2022/10/21/introducing-spring-modulith)
    - [Spring Modulith - Reference documentation](https://docs.spring.io/spring-modulith/docs/current-SNAPSHOT/reference/html/)

````
  url: jdbc:postgresql://localhost:5432/jira
  username: jira
  password: JiraRush
````

- Є 2 загальні таблиці, на яких не fk
    - _Reference_ – довідник. Зв'язок робимо по _code_ (за id не можна, тк id прив'язано до оточення-конкретної бази)
    - _UserBelong_ - прив'язка користувачів із типом (owner, lead, ...) до об'єкту (таска, проєкт, спринт, ...). FK вручну будемо
      перевіряти

## Аналоги

- https://java-source.net/open-source/issue-trackers

## Тестування

- https://habr.com/ua/articles/259055/

Список виконаних завдань:
1. Розібрався зі структурою проекту.
2. Видалив соціальні мережі: vk, yandex.
3. Виніс чутливу інформацію до окремого проперті файлу config/conf.properties:
   - логін
   - пароль БД
   - ідентифікатори для OAuth реєстрації/авторизації
   - налаштування пошти
4. Додав окремий профіль test суто для тестів. 
   Переробив тести так, щоб під час тестів використовувалася in memory БД (H2), а не PostgreSQL.
5. Зробив рефакторинг методу com.javarush.jira.bugtracking.attachment.FileUtil#upload, щоб він використовував сучасний підхід для роботи з файловою системою. 
Використав NIO.