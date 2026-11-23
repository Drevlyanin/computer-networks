# Команди лабораторної роботи

## Перевірка Docker

```bash
docker version
docker ps -a
```

## Amazon Linux 2023

```bash
docker pull amazonlinux:2023
docker run -it --name student_amazon amazonlinux:2023 bash
cat /etc/os-release
```

## Тестовий контейнер

```bash
docker run hello-world
docker ps
docker ps -a
```

## Образи варіанта 25

```bash
docker pull httpd:2.4
docker pull mongo:8
docker pull eclipse-temurin:21-jdk-alpine
docker images

docker run --rm httpd:2.4 httpd -v
docker run --rm mongo:8 mongod --version
docker run --rm eclipse-temurin:21-jdk-alpine java -version
```

## Nginx зі спільним каталогом

```bash
mkdir -p /student_project/public_html
cd /student_project
echo "Testing Docker Volumes" > public_html/index.html
docker run --name web_server -d -p 8080:80 -v "$(pwd)/public_html:/usr/share/nginx/html:ro" nginx
curl http://localhost:8080
```

## Керування контейнером

```bash
docker rename web_server student_nginx
docker ps
curl http://localhost:8080

docker stop student_nginx
docker rm student_nginx
docker container prune -f
docker ps -a
```
