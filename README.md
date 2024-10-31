# HTTP_Server

Этот проект представляет собой HTTP-сервер, написанный на Python, который возвращает статус `200 OK` на запрос к `/healthz`. Сервер разворачивается с помощью Docker-контейнера. В рамках данной работы использовалась виртуальная машина Debian 11.

Для развертывания проекта необходимо:
1. Установить docker:
```bash
sudo apt update
sudo apt install apt-transport-https ca-certificates curl software-properties-common -y
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo apt-key add -
echo "deb [arch=amd64] https://download.docker.com/linux/debian $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list
sudo apt update
sudo apt install docker-ce -y
```
2. Клонировать репозиторий и войти в директорию репозитория:
```bash
git clone https://github.com/johnnysvill/HTTP_Server
cd HTTP_Server
```
3. Собрать Docker-образ
```bash
docker build -t http-server .
```
4. Запустить HTTP-сервер в Docker-контейнере:
```bash
docker run -d -p 8000:8000 --name http-server-container http-server
```

Для проверки работы сервера можно отправить запрос с помощью curl:
```bash
curl http://localhost:8000/healthz
```
Или перейти по адресу в браузере:
```bash
http://localhost:8000/healthz
```
