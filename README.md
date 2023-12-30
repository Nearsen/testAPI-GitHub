# testAPI-GitHub

ссылка на REST API GitHub
https://docs.github.com/en/rest/issues/issues?apiVersion=2022-11-28#about-issues

Ссылка на репозиторий
https://github.com/Nearsen/testAPI-GitHub

API ключ
(в прикрепленном readme файле)

Предусловия
Создать аккаунт в GitHub;
Создать репозиторий с произвольным содержимым;

Создать API ключ (персональный токен) в GitHub

Создать коллекцию в Postman

- Добавить токен в закладку Variables коллекции
- Добавить https://api.github.com/repos в закладку Variables коллекции как {{apiGitHub}}
- Добавить название аккаунта (Nearsen) в закладку Variables коллекции как {{owner}}
- Добавить название репозитория (testAPI-GitHub) в закладку Variables коллекции как {{repo}}

API запрос
- https://api.github.com/repos/Nearsen/testAPI-GitHub

-------------------
1. Создать issue 1 
- POST запрос {{apiGitHub}}/{{owner}}/{{repo}}/issues
тело запроса
{
  "title": "issue1",
  "body": "Something went wrong",
  "labels": ["bug"]
}
-------------------
2. получить список issue 
- GET запрос {{apiGitHub}}/{{owner}}/{{repo}}/issues
--------------------
3. Изменить issue 1  
- PATH запрос {{apiGitHub}}/{{owner}}/{{repo}}/issues/1  (где 1 - номер issue. номер issue взять из ответа GET запроса - "number": 1,)
тело запроса
{
  "title": "issue2",
  "body": "Something went wrong",
  "labels": ["bug"]
}
-------------------
4. получить список issue 
- GET запрос {{apiGitHub}}/{{owner}}/{{repo}}/issues 
-----------------
5. Удалить issue 2 
-- в документации REST API GitHub не найдено описание удаления Issue из репозитория (есть изменение, блокировка, разблокировка)
Нашел информацию, что Issue в GitHub можно удалить запросом GraphQL, но мне не это не удалось.

Взамен этого в коллекцию добавил 2 запроса:
- Заблокировать issue
- Удалить репозиторий. (логично же, что вместе с ним удалится и issue))) --
--------

Заблокировать issue 2
- PUT запрос {{apiGitHub}}/{{owner}}/{{repo}}/issues/1/lock  (где 1 - номер issue, номер не меняется в отличие от названия)

Удалить репозиторий
- DELETE запрос {{apiGitHub}}/{{owner}}/{{repo}}
