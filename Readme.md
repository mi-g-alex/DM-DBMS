## Серсис: Зоопарк

### Функциональные требования:

- Аутентификация/авторизация пользователя;
- Управление пользователями (CRUD);
- Система ролей;
- Журналирование действий пользователя;количеству нужных мест;
- Покупка билетов в зоопарк с опциями
- Просмотр информации про животных и сотрудниках


### Сущности базы данных

- **Users:**
    - id (PK)
    - username
    - email
    - password\_hash
    - register\_datetime

------

- **Visitors**
    - id (PK)
    - user_id (FK)
    - first\_name
    - last\_name

- **Ticket**
    - id (PK)
    - visitor\_id (FK)
    - date
    - price

- **ticket_addition_count**
    - id (PK)
    - ticket\_id (FK1)
    - ticket\_addition (FK2)
    - count

- **Addition**
    - id (PK)
    - name
    - price

-----

- **Employee**
    - id (PK)
    - user\_id (FK)
    - last\_name 
    - phone\_number
    - first\_name 

- **Place**
    - id (PK)
    - employee\_id (FK)
    - place\_name
    - square
    - has_swimming

- **Animal**
    - id (PK)
    - name
    - birthday\_date
    - facts
    - place\_id (FK)

- **animal_food_table**
    - id (PK)
    - food\_id (FK1)
    - animal\_id (FK2)
    - count

- **Food**
    - id (PK)
    - name
    - type

### Ненормализованная схема БД:
![Scheme](./DM&DBMS.drawio.svg)

