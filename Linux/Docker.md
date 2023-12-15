# Table of Contents

- [Table of Contents](#table-of-contents)
  - [Download](#download)
  - [Start](#start)
  - [Stop](#stop)
  - [Show containers\&images](#show-containersimages)
  - [Delete](#delete)
  - [Shift storage place](#shift-storage-place)

## Download

Для простоты, можно относиться к образу как к git-репозиторию. Образы можно коммитить с изменениями, и можно иметь несколько версий. Если не указывать конкретную версию, то клиент по умолчанию использует latest. Например, можно скачать определенную версию образа ubuntu:

```bash
docker pull ubuntu:12.04
```

Поиск с:

```bash
docker search NAME
```

## Start

Команда run с флагом -it подключает интерактивный tty в контейнер. Теперь можно запускать сколько угодно много команд внутри:

```bash
docker run -it busybox sh
```

Флаг -d открепит (detach) терминал, флаг -P сделает все открытые порты публичными и случайными, и, наконец, флаг --name это имя, которое мы хотим дать контейнеру:

```bash
docker run -d -P --name static-site busybox
```

Теперь можно увидеть порты с помощью команды docker port [CONTAINER]:

```bash
docker port static-site
```

## Stop

Чтобы остановить контейнер запустите docker stop и укажите идентификатор (ID) контейнера

```bash
docker stop ID
```

## Show containers&images

Теперь виден список всех контейнеров, которые мы запускали. В колонке STATUS можно заметить, что контейнеры завершили свою работу несколько минут назад:

```bash
docker ps -a
```

Чтобы увидеть список доступных локально образов, используйте команду docker images

```bash
docker images
```

## Delete

с помощью команды **docker ps -a** все еще можно увидеть остатки завершенных контейнеров. Для удаления используется команда docker rm. Просто скопируйте ID (можно несколько) из вывода выше и передайте параметрами в команду

```bash
docker rm 305297d7a235 ff0a5c3750b9
```

Если нужно удалить много контейнеров, то вместо ручного копирования и вставления можно сделать так:

```bash
docker rm $(docker ps -a -q -f status=exited)
```

## Shift storage place

To store images onto other as in /var/lib/docker add into /etc/default/docker the following line:

```bash
DOCKER_OPTS="-g /mnt/data/Work/docker"
```

And shift whole /var/lib/docker into /mnt/data/Work/docker
