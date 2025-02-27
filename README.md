# Лабораторная работа: Первый контейнер

## Цель работы

Данная лабораторная работа знакомит с основами контейнеризации и подготавливает рабочее место для выполнения следующих лабораторных работ.

## Задание

1. Установить Docker Desktop и проверить его работоспособность.

2. Создать репозиторий `containers02` и склонировать его себе на компьютер.

3. В папке `containers02` создать файл `Dockerfile` со следующим содержимым:

```Dockerfile
FROM debian:latest
COPY ./site/ /var/www/html/
CMD ["sh", "-c", "echo hello from $HOSTNAME"]
```

4. В той же папке проекта создать папку `site`. В новой папке создать файл `index.html` с произвольным содержимым.

5. Собрать образ с помощью команды:

   ```sh
   docker build -t containers02 .
   ```

6. Запустить контейнер с помощью команды:

   ```sh
   docker run --name containers02 containers02
   ```

7. Удалить контейнер и запустить снова в интерактивном режиме:

   ```sh
   docker rm containers02
   docker run -ti --name containers02 containers02 bash
   ```

8. Внутри контейнера выполнить:
   
   ```sh
   cd /var/www/html/
   ls -l
   ```

9. Закрыть окно контейнера с помощью команды `exit`.

## Описание выполнения работы

### Установка Docker Desktop

Docker Desktop был установлен согласно официальной документации. Проверена его работоспособность командой:

```sh
docker --version
```

![image](https://i.imgur.com/HeqHzLo.png)

Выведена версия Docker, подтверждающая успешную установку.

### Создание репозитория и подготовка файлов

1. Репозиторий `containers02` был создан и клонирован локально.

![image](https://i.imgur.com/YEcrUGq.png)

2. Внутри `containers02` был создан `Dockerfile` с требуемым содержимым.

![image](https://i.imgur.com/Nrl71us.png)

3. Создана папка `site`, в которой был размещён `index.html` с произвольным содержимым.

![image](https://i.imgur.com/iJD8OJg.png)

### Сборка образа

Команда `docker build -t containers02 .` успешно собрала образ.

![image](https://i.imgur.com/5oufIM6.png)

**Время создания образа:**

Сборка образа заняла 79.6 секунд, что подтверждается выводом команды.

### Запуск контейнера

После выполнения команды `docker run --name containers02 containers02` в консоли было выведено сообщение:

```sh
hello from ba2bb067677d
```

![image](https://i.imgur.com/7zxDt1H.png)

### Проверка содержимого контейнера

После удаления контейнера и запуска в интерактивном режиме:

```sh
docker rm containers02
docker run -ti --name containers02 containers02 bash
```

Затем внутри контейнера:

```sh
cd /var/www/html/
ls -l
```

![image](https://i.imgur.com/GGbOe6u.png)

**Вывод в консоли:**

```sh
<список файлов, включая index.html>
```

![image](https://i.imgur.com/dK4pp3O.png)

Это подтверждает, что файл `index.html` был успешно скопирован в контейнер.

**Закрываем окно:**

![image](https://i.imgur.com/ma3Wh5A.png)

## Выводы

В ходе выполнения лабораторной работы была установлена и настроена среда Docker Desktop. Создан и собран образ на основе `debian:latest`, содержащий подготовленный сайт. После запуска контейнера было проверено, что файлы корректно передаются в `/var/www/html/`. Контейнер успешно выполнял заданные команды и корректно обрабатывал содержимое.

Также была получена практика работы с Docker, включая создание образов, управление контейнерами и работу в интерактивном режиме. Полученные знания и навыки пригодятся в дальнейших лабораторных работах и при использовании контейнеризации в реальных проектах.

## Используемые источники

- [Официальная документация Docker](https://docs.docker.com/)
- [Docker Hub](https://hub.docker.com/)
- [Учебное руководство по Docker](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-20-04)
- [Руководство по написанию Dockerfile](https://docs.docker.com/engine/reference/builder/)
