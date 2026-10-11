# Tournament Tracker API

## Опис ідеї
**Tournament Tracker** - це платформа для створення, управління та відстеження студентських кіберспортивних турнірів. Сайт дозволяє організаторам створювати турніри, реєструвати команди та гравців, керувати розкладом матчів і оновлювати турнірні сітки та результати ігор. Користувачі можуть переглядати актуальні матчі, склади команд і статистику.

## Архітектура REST API

### Турніри

* **Отримати список усіх турнірів**
  * **Method:** GET
  * **Parameters:** status
  * **Response Status:** 200 OK
  * **Response Body:**
    ```json
    [
      {
        "id": 1,
        "title": "CS2 Student Cup",
        "game": "Counter-Strike 2",
        "status": "active"
      }
    ]
    ```

* **Створити новий турнір**
  * **Method:** POST
  * **Request Body:**
    ```json
    {
      "title": "Dota 2 Autumn Cup",
      "game": "Dota 2",
      "status": "registration"
    }
    ```
  * **Response Status:** 201 Created


### Команди

* **Отримати список команд**
  * **Method:** GET
  * **Parameters:** tournament_id
  * **Response Status:** 200 OK
  * **Response Body:**
    ```json
    [
      {
        "id": 10,
        "name": "CyberCats",
        "tournament_id": 1
      }
    ]
    ```

* **Зареєструвати нову команду**
  * **Method:** POST
  * **Request Body:**
    ```json
    {
      "name": "CodeBreakers",
      "tournament_id": 1
    }
    ```
  * **Response Status:** 201 Created

### Матчі

* **Отримати розклад матчів**
  * **Method:** GET
  * **Parameters:** tournament_id
  * **Response Status:** 200 OK
  * **Response Body:**
    ```json
    [
      {
        "match_id": 101,
        "team_1": "CyberCats",
        "team_2": "CodeBreakers",
        "score": "2:1",
        "status": "completed"
      }
    ]
    ```

## Схема бази даних
![схема бази даних](image.png)