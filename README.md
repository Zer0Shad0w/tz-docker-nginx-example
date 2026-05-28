# tz-docker-nginx-example

* это минимальный контейнеризированный веб-проект, построенный по архитектуре reverse proxy.
  Проект работает по структуре Клиент → Nginx → Python backend.

## Как работает?

1. Клиент подключается подключается по [http://localhost](http://localhost) с указанным портом
2. Запрос принимает Nginx
3. Nginx проксирует запрос во внутренюю docker-сеть по адресу backend:8080
4. Python http сервер возвращает ответ: "Hello from Effectrive Mobile!"
5. Ответ python-скрипта возвращается через Nginx пользователю

## Установка:

* Скачать и запустить docker в системе:

### Fedora:

`sudo dnf install -y docker docker docker-compose-plugin`

### Debian/Ubuntu/LMDE:

`sudo apt update && sudo apt install -y docker.io docker-compose-plugin`

### Arch:

`sudo pacman -S docker docker-compose`

### Запуск для вышеуказанных и других систем использующих systemd:

`sudo systemctl enable --now docker`

### Alpine Linux:

`sudo apk add docker docker-cli-compose
sudo rc-service docker start
sudo rc-update add docker`

### Проверка:

`docker --version`

---

## (Опционально) Добавление пользователя в докер группу для запуска docker-контейнера без sudo:

`newgrp docker
sudo usermod -aG docker $USER`

---

## Склонировать репозиторий и войти в него

`git clone [https://github.com/Zer0Shad0w/tz-docker-nginx-example.git](https://github.com/Zer0Shad0w/tz-docker-nginx-example.git) && cd tz-docker-nginx-example`

---

## В корне проекта создать файл .env

`NGINX_PORT=8080 # вместо 8080 можно указать незанятый желаемый порт`

---

## Запуск приложения

`docker-compose up --build`

---

## Запуск приложение в качестве даемона

`docker-compose up --build -d`

## Для остановки в таком случае

`docker-compose down`

---

Теперь localhost с указанным портом будет выдавать работу backend'а

[http://localhost](http://localhost):<NGINX_PORT>

* сделано Zer0Shad0w
