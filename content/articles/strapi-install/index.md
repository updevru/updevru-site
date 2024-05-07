---
title: "Strapi - установка и настройка"
type: post
tags: ["Strapi"]
date: 2024-04-25T19:30:00+03:00
showTableOfContents: true
image: "/articles/strapi-install/cover.png"
---

![](cover.png)

[Strapi](https://strapi.io/) - популярная open-source headless CMS.
Написана на JavaScript/TypeScript, максимально настраивается под ваши задачи.

Данная CMS создана для разработчиков, она делает множество рутинной работы, позволяя сосредоточится на бизнес логике.
Подходит для широкого спектра задач - блоги, порталы, каталоги, сервисы, магазины и многое другое.

## Создание проекта

Исчерпывающая инструкция на [официальном сайте](https://docs.strapi.io/dev-docs/installation/cli),
тут я приведу краткий набор команд и действия. Демо приложение будет находиться в папке strapi.

Перед установкой у вас должно быть:
- Node.js версия v18 или v20
- npm или yarn
- Python

Создание проекта:

```
npx create-strapi-app@latest strapi
```

После выполнения запускаем в режиме разработки и создаем наш набор данных.

```
npm run develop
```

Для локальной разработки этого, как правило, достаточно.

## Конфигурация и сборка проекта

После установки и создание структуры данных для запуска проекта на сервере мы будем использовать Docker.
Это очень универсальный способ, который позволит запустить наше приложение как в облаке, так и на сервере.

Убедитесь что у вас установлен [Docker](https://www.docker.com/) и [Docker Compose](https://docs.docker.com/compose/).

Добавляем Dockerfile в наш проект с содержимым:

```dockerfile
FROM node:20-alpine as build
# Installing libvips-dev for sharp Compatibility
RUN apk update && apk add build-base gcc autoconf automake zlib-dev libpng-dev vips-dev && rm -rf /var/cache/apk/* > /dev/null 2>&1
ARG NODE_ENV=production
ENV NODE_ENV=${NODE_ENV}

WORKDIR /opt/app
COPY package.json .
COPY package-lock.json .

RUN npm install --force

COPY .. .
RUN npm run build


FROM node:20-alpine
# Installing libvips-dev for sharp Compatibility
RUN apk add vips-dev
RUN rm -rf /var/cache/apk/*

ARG NODE_ENV=production
ENV NODE_ENV=${NODE_ENV}

WORKDIR /opt/app
COPY --from=build /opt/app ./

EXPOSE 1337
CMD ["npm", "run","start"]
```

Переходим в папку `strapi` с проектом и проверяем что сборка работает.

```
docker build -t strapi .
```

Запускаем контейнер, для запуска потребуется указать реквизиты сервера базы данных.
Ниже команда для примера, необходимо указать свои.

```
docker run -p 1337:1337 \ 
    -e DATABASE_CLIENT=postgres \ 
    -e DATABASE_HOST=127.0.0.1 \
    -e DATABASE_PORT=5432 \
    -e DATABASE_NAME=strapi \ 
    -e DATABASE_USERNAME=strapi \ 
    -e DATABASE_PASSWORD=strapi \
    strapi
```

## Публикация Docker образа

Для запуска контейнера из нашего образа на удаленном сервере - необходимо загрузить образ в registry.

### Docker Hub

Публичные образы можно загружать туда бесплатно, а для приватных нужна платная подписка.

Необходимо [создать аккаунт](https://docs.docker.com/docker-hub/quickstart/),
если у вас его еще нет, и [авторизоваться под ним](https://docs.docker.com/reference/cli/docker/login/).

После этого можно собрать образ и загрузить в реестр. Название образа обязательно должно в формате `логин/название:версия`.

```
docker build -t updev/strapi:1.0 .
docker push updev/strapi:1.0
```

### Yandex Container Registry

Реестр Яндекса платный, но стоимость достаточно низкая и зависит от размера хранящихся там образов.

Инструкция как создать реестр и авторизоваться [тут](https://yandex.cloud/ru/docs/container-registry/quickstart/).
После создания у вас будет реестр с уникальным именем, например cr.yandex/crpoe5.....8h9al8r0/strapi

```
docker build -t cr.yandex/crpoe5.....8h9al8r0/strapi:1.0 .
docker push cr.yandex/crpoe5.....8h9al8r0/strapi:1.0
```

Исходный код руководства на [GitHub](https://github.com/updevru/tutorial-strapi-deploy).