##Чек-листы для API регистрации пользователей (melivecode)

- **Регистрация**:
  - Корректность статус-кода (200 ОК).
  - Корректность тела ответа.
  - Корректность ID.
  - Корректность времени ответа (менее 500 мс).
  - Корректность заголовков ответа.
  - Регистрация с отсутствующими заголовками.
  - Регистрация с неверным методом HTTP (GET).
  - Регистрация через HTTP вместо HTTPS.
  - Регистрация с пустым телом запроса.
  - Проверка SQL-инъекции в обоих полях.
  - Регистрация с телом запроса в формате JSON и Content-type: application/JavaScript.

- **Email**:
  - Корректная обработка email с различными доменами (например, @gmail.com).
  - Регистрация с email, содержащим допустимые спецсимволы.
  - Регистрация с email, состоящим из цифр.
  - Регистрация с email, состоящим из символов верхнего регистра (латиница).
  - Регистрация с email, состоящим из спецсимволов, цифр, латиницы верхнего и нижнего регистра.
  - Регистрация с email, содержащим минимальное количество символов (1 символ, не включая домен).
  - Регистрация с email, содержащим максимальное количество символов (15 символов, не включая домен).
  - Регистрация с некорректным email.
  - Регистрация с существующим email.
  - Регистрация с email, состоящим из кириллицы.
  - Проверка SQL-инъекции в поле email.
  - Регистрация с пустым полем email.
  - Регистрация с email без доменной части.
  - Регистрация с email длиной больше допустимой (16 символов).
  - Регистрация с email, состоящим только из цифр.
  - Регистрация с email, состоящим из домена.

- **Пароль**:
  - Регистрация с минимальной длиной пароля (4 символа).
  - Регистрация с паролем, состоящим из спецсимволов.
  - Регистрация с паролем, состоящим из цифр.
  - Регистрация с паролем, состоящим из символов верхнего регистра (латиница).
  - Регистрация с паролем, состоящим из кириллицы.
  - Проверка SQL-инъекции в поле пароля.
  - Регистрация с длиной пароля меньше допустимой (3 символа).
  - Регистрация с паролем, содержащим только пробелы.
  - Регистрация с пустым полем пароля.

## Тест-кейсы для API регистрации пользователей (melivecode)

## **1. Регистрация нового пользователя с валидными данными**
- **Шаги**:
  1. Отправить запрос методом POST на `https://www.melivecode.com/api/users/create` с телом запроса:
     ```json
     {
       "email": "cat.chat@melvecode.com",
       "password": "1234"
     }
     ```
- **Ожидаемый результат**:
  - Код состояния: `200 OK`
  - Тело ответа:
    ```json
    {
      "status": "ok",
      "message": "User with ID = 14 is created",
      "user": {
        "id": 14,
        "email": "cat.chat@melvecode.com"
      }
    }
    ```

---

## **2. Регистрация нового пользователя с доменом в email (@gmail.com)**
- **Шаги**:
  1. Отправить запрос методом POST на `https://www.melivecode.com/api/users/create` с телом запроса:
     ```json
     {
       "email": "cat.chat@gmail.com",
       "password": "1234"
     }
     ```
- **Ожидаемый результат**:
  - Код состояния: `200 OK`
  - Тело ответа:
    ```json
    {
      "status": "ok",
      "message": "User with ID = 13 is created",
      "user": {
        "id": 13,
        "email": "cat.chat@gmail.com"
      }
    }
    ```

---

## **3. Регистрация нового пользователя с email, содержащим допустимые спецсимволы**
- **Шаги**:
  1. Отправить запрос методом POST на `https://www.melivecode.com/api/users/create` с телом запроса:
     ```json
     {
       "email": "cat.and.dog,s_@gmail.com",
       "password": "1234"
     }
     ```
- **Ожидаемый результат**:
  - Код состояния: `200 OK`
  - Тело ответа:
    ```json
    {
      "status": "ok",
      "message": "User with ID = 15 is created",
      "user": {
        "id": 15,
        "email": "cat.and.dog,s_@gmail.com"
      }
    }
    ```

---

## **4. Регистрация нового пользователя с email, состоящим из цифр**
- **Шаги**:
  1. Отправить запрос методом POST на `https://www.melivecode.com/api/users/create` с телом запроса:
     ```json
     {
       "email": "1234@gmail.com",
       "password": "1234"
     }
     ```
- **Ожидаемый результат**:
  - Код состояния: `200 OK`
  - Тело ответа:
    ```json
    {
      "status": "ok",
      "message": "User with ID = 16 is created",
      "user": {
        "id": 16,
        "email": "1234@gmail.com"
      }
    }
    ```

---

## **5. Регистрация нового пользователя с email, состоящим из символов верхнего регистра (латиница)**
- **Шаги**:
  1. Отправить запрос методом POST на `https://www.melivecode.com/api/users/create` с телом запроса:
     ```json
     {
       "email": "CATSANDDOGS@gmail.com",
       "password": "1234"
     }
     ```
- **Ожидаемый результат**:
  - Код состояния: `200 OK`
  - Тело ответа:
    ```json
    {
      "status": "ok",
      "message": "User with ID = 17 is created",
      "user": {
        "id": 17,
        "email": "CATSANDDOGS@gmail.com"
      }
    }
    ```

---

## **6. Регистрация нового пользователя с email, состоящим из спецсимволов, цифр, латиницы верхнего и нижнего регистра**
- **Шаги**:
  1. Отправить запрос методом POST на `https://www.melivecode.com/api/users/create` с телом запроса:
     ```json
     {
       "email": "2CATS.and_1DOGS@gmail.com",
       "password": "1234"
     }
     ```
- **Ожидаемый результат**:
  - Код состояния: `200 OK`
  - Тело ответа:
    ```json
    {
      "status": "ok",
      "message": "User with ID = 18 is created",
      "user": {
        "id": 18,
        "email": "2CATS.and_1DOGS@gmail.com"
      }
    }
    ```

---

## **7. Регистрация нового пользователя с email, содержащим минимальное количество символов**
- **Шаги**:
  1. Отправить запрос методом POST на `https://www.melivecode.com/api/users/create` с телом запроса:
     ```json
     {
       "email": "d@gmail.com",
       "password": "1234"
     }
     ```
- **Ожидаемый результат**:
  - Код состояния: `200 OK`
  - Тело ответа:
    ```json
    {
      "status": "ok",
      "message": "User with ID = 19 is created",
      "user": {
        "id": 19,
        "email": "d@gmail.com"
      }
    }
    ```

---

## **8. Регистрация нового пользователя с email, содержащим максимальное количество символов**
- **Шаги**:
  1. Отправить запрос методом POST на `https://www.melivecode.com/api/users/create` с телом запроса:
     ```json
     {
       "email": "ddasdasdasdasda@gmail.com",
       "password": "1234"
     }
     ```
- **Ожидаемый результат**:
  - Код состояния: `200 OK`
  - Тело ответа:
    ```json
    {
      "status": "ok",
      "message": "User with ID = 20 is created",
      "user": {
        "id": 20,
        "email": "ddasdasdasdasda@gmail.com"
      }
    }
    ```

---

## **9. Регистрация нового пользователя с password, содержащим минимальное количество символов**
- **Шаги**:
  1. Отправить запрос методом POST на `https://www.melivecode.com/api/users/create` с телом запроса:
     ```json
     {
       "email": "catsanddogs@gmail.com",
       "password": "qwer"
     }
     ```
- **Ожидаемый результат**:
  - Код состояния: `200 OK`
  - Тело ответа:
    ```json
    {
      "status": "ok",
      "message": "User with ID = 21 is created",
      "user": {
        "id": 21,
        "email": "catsanddogs@gmail.com"
      }
    }
    ```

---

## **10. Регистрация нового пользователя с password, состоящим из символов верхнего регистра (латиница)**
- **Шаги**:
  1. Отправить запрос методом POST на `https://www.melivecode.com/api/users/create` с телом запроса:
     ```json
     {
       "email": "catsandddogs@gmail.com",
       "password": "QWERTY"
     }
     ```
- **Ожидаемый результат**:
  - Код состояния: `200 OK`
  - Тело ответа:
    ```json
    {
      "status": "ok",
      "message": "User with ID = 22 is created",
      "user": {
        "id": 22,
        "email": "catsandddogs@gmail.com"
      }
    }
    ```

---

## **11. Регистрация нового пользователя с password, состоящим из кириллицы**
- **Шаги**:
  1. Отправить запрос методом POST на `https://www.melivecode.com/api/users/create` с телом запроса:
     ```json
     {
       "email": "catsaogs@gmail.com",
       "password": "кверти"
     }
     ```
- **Ожидаемый результат**:
  - Код состояния: `200 OK`
  - Тело ответа:
    ```json
    {
      "status": "ok",
      "message": "User with ID = 23 is created",
      "user": {
        "id": 23,
        "email": "catsaogs@gmail.com"
      }
    }
    ```

---

## **12. Регистрация нового пользователя с отсутствующими заголовками**
- **Шаги**:
  1. Отправить запрос методом POST на `https://www.melivecode.com/api/users/create` с телом запроса:
     ```json
     {
       "email": "1c2c@gmail.com",
       "password": "1234"
     }
     ```
- **Ожидаемый результат**:
  - Код состояния: `400 Bad Request`
  - Тело ответа:
    ```json
    {
      "status": "error"
    }
    ```

---

## **13. Регистрация нового пользователя с использованием метода GET**
- **Шаги**:
  1. Отправить запрос методом GET на `https://www.melivecode.com/api/users/create` с телом запроса:
     ```json
     {
       "email": "1c2c@gmail.com",
       "password": "1234"
     }
     ```
- **Ожидаемый результат**:
  - Код состояния: `404 Not Found`
  - Тело ответа:
    ```json
    {
      "status": "error"
    }
    ```

---

## **14. Регистрация нового пользователя с использованием протокола HTTP**
- **Шаги**:
  1. Отправить запрос методом POST на `http://www.melivecode.com/api/users/create` с телом запроса:
     ```json
     {
       "email": "1c2c@gmail.com",
       "password": "1234"
     }
     ```
- **Ожидаемый результат**:
  - Код состояния: `404 Not Found`
  - Тело ответа:
    ```json
    {
      "status": "error"
    }
    ```

---

## **15. Регистрация нового пользователя с пустым телом запроса**
- **Шаги**:
  1. Отправить запрос методом POST на `https://www.melivecode.com/api/users/create` с пустым телом запроса.
- **Ожидаемый результат**:
  - Код состояния: `404 Not Found`
  - Тело ответа:
    ```json
    {
      "status": "error"
    }
    ```

---

## **16. Регистрация нового пользователя с использованием SQL-инъекции в поле email**
- **Шаги**:
  1. Отправить запрос методом POST на `https://www.melivecode.com/api/users/create` с телом запроса:
     ```json
     {
       "email": "user' or 1 = 1 --",
       "password": "1234"
     }
     ```
- **Ожидаемый результат**:
  - Код состояния: `200 OK`
  - Тело ответа:
    ```json
    {
      "status": "ok",
      "message": "User with ID = 24 is created",
      "user": {
        "id": 24,
        "email": "user' or 1 = 1 --"
      }
    }
    ```

---

## **17. Регистрация нового пользователя с использованием Content-type: application/javascript**
- **Шаги**:
  1. Отправить запрос методом POST на `https://www.melivecode.com/api/users/create` с заголовком `Content-type: application/javascript` и телом запроса:
     ```json
     {
       "email": "fdsfsf@gmail.com",
       "password": "1234"
     }
     ```
- **Ожидаемый результат**:
  - Код состояния: `400 Bad Request`
  - Тело ответа:
    ```json
    {
      "status": "error"
    }
    ```

---

## **18. Регистрация нового пользователя с некорректным email**
- **Шаги**:
  1. Отправить запрос методом POST на `https://www.melivecode.com/api/users/create` с телом запроса:
     ```json
     {
       "email": "fdsfsf@gmailcom",
       "password": "1234"
     }
     ```
- **Ожидаемый результат**:
  - Код состояния: `200 OK`
  - Тело ответа:
    ```json
    {
      "status": "ok",
      "message": "User with ID = 24 is created",
      "user": {
        "id": 24,
        "email": "fdsfsf@gmailcom"
      }
    }
    ```

---

## **19. Регистрация нового пользователя с существующим email**
- **Шаги**:
  1. Отправить запрос методом POST на `https://www.melivecode.com/api/users/create` с телом запроса:
     ```json
     {
       "email": "catsaogs@gmailcom",
       "password": "кверти"
     }
     ```
- **Ожидаемый результат**:
  - Код состояния: `200 OK`
  - Тело ответа:
    ```json
    {
      "status": "error",
      "message": "user exists"
    }
    ```

---

## **20. Регистрация нового пользователя с email, состоящим из кириллицы**
- **Шаги**:
  1. Отправить запрос методом POST на `https://www.melivecode.com/api/users/create` с телом запроса:
     ```json
     {
       "email": "кверти@gmailcom",
       "password": "1234"
     }
     ```
- **Ожидаемый результат**:
  - Код состояния: `200 OK`
  - Тело ответа:
    ```json
    {
      "status": "ok",
      "message": "User with ID = 25 is created",
      "user": {
        "id": 25,
        "email": "кверти@gmailcom"
      }
    }
    ```

---

## **21. Регистрация нового пользователя с пустым полем email**
- **Шаги**:
  1. Отправить запрос методом POST на `https://www.melivecode.com/api/users/create` с телом запроса:
     ```json
     {
       "email": "",
       "password": "1234"
     }
     ```
- **Ожидаемый результат**:
  - Код состояния: `400 Bad Request`
  - Тело ответа:
    ```json
    {
      "status": "error",
      "message": "Missing fields"
    }
    ```

---

## **22. Регистрация нового пользователя с email без доменной части**
- **Шаги**:
  1. Отправить запрос методом POST на `https://www.melivecode.com/api/users/create` с телом запроса:
     ```json
     {
       "email": "dandadan",
       "password": "1234"
     }
     ```
- **Ожидаемый результат**:
  - Код состояния: `200 OK`
  - Тело ответа:
    ```json
    {
      "status": "ok",
      "message": "User with ID = 26 is created",
      "user": {
        "id": 26,
        "email": "dandadan"
      }
    }
    ```

---

## **23. Регистрация нового пользователя с длиной символов в password больше допустимой**
- **Шаги**:
  1. Отправить запрос методом POST на `https://www.melivecode.com/api/users/create` с телом запроса:
     ```json
     {
       "email": "raincats@gmail.com",
       "password": "ddasdasdasdasdaa"
     }
     ```
- **Ожидаемый результат**:
  - Код состояния: `400 Bad Request`
  - Тело ответа:
    ```json
    {
      "status": "error"
    }
    ```

---

## **24. Регистрация нового пользователя с email, состоящим из цифр**
- **Шаги**:
  1. Отправить запрос методом POST на `https://www.melivecode.com/api/users/create` с телом запроса:
     ```json
     {
       "email": "123456@gmail.com",
       "password": "ddasdasdasdasdaa"
     }
     ```
- **Ожидаемый результат**:
  - Код состояния: `400 Bad Request`
  - Тело ответа:
    ```json
    {
      "status": "error"
    }
    ```

---

## **25. Регистрация нового пользователя с использованием SQL-инъекции в поле password**
- **Шаги**:
  1. Отправить запрос методом POST на `https://www.melivecode.com/api/users/create` с телом запроса:
     ```json
     {
       "email": "abcd@gmail.com",
       "password": "user' or 1 = 1 --"
     }
     ```
- **Ожидаемый результат**:
  - Код состояния: `200 OK`
  - Тело ответа:
    ```json
    {
      "status": "ok",
      "message": "User with ID = 26 is created",
      "user": {
        "id": 26,
        "email": "abcd@gmail.com"
      }
    }
    ```

---

## **26. Регистрация нового пользователя с длиной password меньше минимальной**
- **Шаги**:
  1. Отправить запрос методом POST на `https://www.melivecode.com/api/users/create` с телом запроса:
     ```json
     {
       "email": "abcde@gmail.com",
       "password": "123"
     }
     ```
- **Ожидаемый результат**:
  - Код состояния: `400 Bad Request`
  - Тело ответа:
    ```json
    {
      "status": "error"
    }
    ```

---

## **27. Регистрация нового пользователя с password, состоящим из пробелов**
- **Шаги**:
  1. Отправить запрос методом POST на `https://www.melivecode.com/api/users/create` с телом запроса:
     ```json
     {
       "email": "abcde@gmail.com",
       "password": "     "
     }
     ```
- **Ожидаемый результат**:
  - Код состояния: `200 OK`
  - Тело ответа:
    ```json
    {
      "status": "ok",
      "message": "User with ID = 27 is created",
      "user": {
        "id": 27,
        "email": "abcdе@gmail.com"
      }
    }
    ```

---

## **28. Регистрация нового пользователя с пустым полем password**
- **Шаги**:
  1. Отправить запрос методом POST на `https://www.melivecode.com/api/users/create` с телом запроса:
     ```json
     {
       "email": "abcde@gmail.com",
       "password": ""
     }
     ```
- **Ожидаемый результат**:
  - Код состояния: `400 Bad Request`
  - Тело ответа:
    ```json
    {
      "status": "error"
    }
    ```

---
