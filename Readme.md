## Серсис: Зоопарк

### Функциональные требования:

- Аутентификация пользователя;
- Управление пользователями (CRUD);
- Система ролей;
- Журналирование действий пользователя;
- Добавление билетов в корзину, изменение количестве, "оплата"
- Добавления дополнительных услуг при копке билета

- Просмотр информации про животных (имя, место, возраст, факты, питание)
- Изменение данных о питании, месте обитании и фактах живного
- Фильтрация животных по имени, месту обитания, еде
- Просмотр инфомрации о сотрудниках (Фамилия Имя, номер телефона, email, должность)
- Изменении должности сотруднков и мест, к которым они прикреплены
- Просмотр информации о месте (какие животные обитают, площадь и т. д.)
- Изменение информации о месте (какие животные обитают, какие сотрудники прикреплены)


### Сущности базы данных

- **Users**
    - id: UUID (PK)
    - username: varchar(15), NOT NULL
    - email: string, NOT NULL
    - password\_hash, NOT NULL
    - register\_datetime, NOT NULL

- **Role**
    - id: Int (PK)
    - role: enum("visitor", "admin", "employee") NOT NULL
    - user\_id: UUID (FK)

------

- **Ticket**
    - id: UUID (PK)
    - visitor\_id: UUID (FK), NOT NULL
    - date: DateField, NOT NULL
    - price: Decimal, NOT NULL
    - is_paid: Boolean, DEFAULT FALSE

- **ticket_addition_count** CHECK (count > 0)
    - id (PK)
    - ticket\_id: UUID (FK1), NOT NULL
    - addition\_id (FK2), NOT NULL
    - count: Int, NOT NULL

- **Addition** CHECK price > 0
    - id: Int (PK)
    - name: String, NOT NULL
    - price: Decimal, NOT NULL, 

-----

- **Employee**
    - id: Int (PK)
    - user\_id: UUID (FK)
    - last\_name: String
    - phone\_number: varchar(12)
    - first\_name: String
    - post: String

- **Place** CHECK square > 0
    - id: Int (PK)
    - employee\_id: Int (FK)
    - place\_name: varchar(30), NOT NULL
    - square: Decimal
    - has_swimming: Boolean, NOT NULL

- **Animal**
    - id (PK)
    - name: varchar(30), NOT NULL
    - birthday\_date: DateField, NOT NULL
    - facts: String, NULL
    - place\_id: Int (FK)

- **animal_food_table** CHECK count > 0
    - id: Int (PK)
    - food\_id: Int (FK1)
    - animal\_id: Int (FK2)
    - count: Decimal

- **Food**
    - id (PK)
    - name: String, NOT NULL
    - type: emum("meat", "fish", "tree")

### Ненормализованная схема БД:
![Scheme](./DM&DBMS.drawio.svg)

