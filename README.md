[![CI/CD](https://github.com/GulaiymNazarova/todo-app/actions/workflows/ci.yml/badge.svg)](https://github.com/GulaiymNazarova/todo-app/actions/workflows/ci.yml)
Todo-app
Учебный проект с настроенным CI/CD пайплайном.



# ToDo App - Лабораторная работа 3 (CI/CD)

[![CI/CD](https://github.com/GulaiymNazarova/todo-app/actions/workflows/ci.yml/badge.svg)](https://github.com/GulaiymNazarova/todo-app/actions/workflows/ci.yml)

**Ссылка на Docker Hub:** https://hub.docker.com/r/gulaiymnazarova/todo-app

## Ответы на вопросы:

**1. Какой тест упал в части 3 и что было в логе?**
В части 3 я специально изменила в файле `app/main.py` ответ эндпоинта `/health` со `"ok"` на `"OK"`. В логах GitHub Actions упал тест `test_health` с ошибкой `AssertionError`. В логе было написано, что тест ожидал `{"status": "ok"}`, а получил `{"status": "OK"}`.

**2. Почему в части 7 (в Pull Request) job build-and-push была пропущена (skipped)?**
В файле конфигурации `ci.yml` у задачи `build-and-push` задано условие `if: github.ref_name == 'main' && github.event_name != 'pull_request'`. Это значит, что сборка и публикация Docker-образа запускаются только при пуше в главную ветку `main`. Для Pull Request эта задача пропускается.

**3. Зачем нужен тег с SHA коммита, если есть latest?**
Тег `latest` всегда указывает на последнюю версию образа. Если выйдет новая версия, `latest` перезапишется. Тег с SHA коммита уникален для каждого конкретного коммита. Он позволяет всегда точно узнать, из какого именно кода был собран этот Docker-образ.


