## ТЗ

Реализовать тайм-трекер

1. Выставить REST методы
Получение данных пользователей:
Фильтрация по всем полям.
Пагинация.
Получение трудозатрат по пользователю за период задача-сумма часов и минут с сортировкой от большей затраты к меньшей
Начать отсчет времени по задаче для пользователя
Закончить отсчет времени по задаче для пользователя
Удаление пользователя
Изменение данных пользователя
Добавление нового пользователя в формате:
```json
{
	"passportNumber": "1234 567890" // серия и номер паспорта пользователя
}
```
2. При добавлении сделать запрос в АПИ, описанного сваггером
```yaml
openapi: 3.0.3
info:
  title: People info
  version: 0.0.1
paths:
  /info:
    get:
      parameters:
        - name: passportSerie
          in: query
          required: true
          schema:
            type: integer
        - name: passportNumber
          in: query
          required: true
          schema:
            type: integer
      responses:
        '200':
          description: Ok
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/People'
        '400':
          description: Bad request
        '500':
          description: Internal server error
components:
  schemas:
    People:
      required:
        - surname
        - name
        - address
      type: object
      properties:
        surname:
          type: string
          example: Иванов
        name:
          type: string
          example: Иван
        patronymic:
          type: string
          example: Иванович
        address:
          type: string
          example: г. Москва, ул. Ленина, д. 5, кв. 1
```
3. Обогащенную информацию положить в БД postgres (структура БД должна быть создана путем миграций при старте сервиса)
4. Покрыть код debug- и info-логами
5. Вынести конфигурационные данные в .env-файл
6. Сгенерировать сваггер на реализованное АПИ



### Start the web server:

   revel run myapp

### Go to http://localhost:9000/ and you'll see:

    "It works"

## Code Layout

The directory structure of a generated Revel application:

    conf/             Configuration directory
        app.conf      Main app configuration file
        routes        Routes definition file

    app/              App sources
        init.go       Interceptor registration
        controllers/  App controllers go here
        views/        Templates directory

    messages/         Message files

    public/           Public static assets
        css/          CSS files
        js/           Javascript files
        images/       Image files

    tests/            Test suites


## Help

* The [Getting Started with Revel](http://revel.github.io/tutorial/gettingstarted.html).
* The [Revel guides](http://revel.github.io/manual/index.html).
* The [Revel sample apps](http://revel.github.io/examples/index.html).
* The [API documentation](https://godoc.org/github.com/revel/revel).

