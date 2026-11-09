# Домашнее задание к занятию 16 «Платформа мониторинга Sentry»

## Задание 1
Создан аккаунт через GitHub, выбран Free-план. Создан проект на Python.

**Скриншот меню Projects:**
![Projects](https://github.com/user-attachments/assets/858ed806-e2e0-43b4-a468-1c51a79390d1)

---

## Задание 2
Сгенерировано тестовое событие ZeroDivisionError. Изучена информация, событие переведено в статус Resolved.

**Скриншот Stack trace:**
![Stack trace](https://github.com/user-attachments/assets/0b40c098-60bb-42ff-abd7-dea1fa357a3d)

**Скриншот списка событий после Resolved:**
![Issues after resolve](https://github.com/user-attachments/assets/1efae60f-0fc3-4348-827f-1329181565c3)

---

## Задание 3
Создано правило алёртинга с настройками по умолчанию (через уведомление участника). После генерации события на почту пришло оповещение.

**Скриншот тела письма:**
![Alert email](https://github.com/user-attachments/assets/75cf6ddb-8698-4438-a86c-4dd5d65d1c6a)

![](https://github.com/user-attachments/assets/5aefa598-ea4b-4d8d-bbf9-ab3cff0ded3c)

![](https://github.com/user-attachments/assets/6445ca3b-1821-4f45-ac35-98346a6a8f81)

---

## Задание повышенной сложности
Создан скрипт на Python, подключен Sentry SDK (`sentry-sdk`), отправлены сообщения и исключения.

**Код скрипта (test.py):**
```python
import sentry_sdk

sentry_sdk.init(
    dsn="https://82dc41875d6284939042aac6edee799e@o4512400861233232.ingest.de.sentry.io/4512400861233232",
    traces_sample_rate=1.0,
)

# Отправляем сообщение
sentry_sdk.capture_message("Тестовое сообщение из домашки", level="info")

# Отправляем ошибку с трассировкой
try:
    1 / 0
except Exception as e:
    sentry_sdk.capture_exception(e)
