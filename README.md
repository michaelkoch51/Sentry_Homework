# Домашнее задание к занятию 16 «Платформа мониторинга Sentry»

## Задание 1
Создан аккаунт через GitHub, выбран Free-план. Создан проект на Python.

**Скриншот меню Projects:**
![Projects]()

---

## Задание 2
Сгенерировано тестовое событие ZeroDivisionError. Изучена информация, событие переведено в статус Resolved.

**Скриншот Stack trace:**
![Stack trace]()

**Скриншот списка событий после Resolved:**
![Issues after resolve]()

---

## Задание 3
Создано правило алёртинга с настройками по умолчанию (через уведомление участника). После генерации события на почту пришло оповещение.

**Скриншот тела письма:**
![Alert email]()

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
