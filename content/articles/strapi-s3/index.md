---
title: "Strapi - Подключение S3 хранилища для файлов"
type: post
tags: ["Strapi"]
date: 2024-05-06T20:00:00+03:00
showTableOfContents: true
image: "/articles/strapi-s3/cover.png"
---

![](cover.png)

Для хранения загружаемых файлов будем использовать S3 хранилище - Yandex Object Storage.
В нем можно дешево хранить файлы и быстро раздавать их через cdn.

Инструкция по [созданию бакета](https://yandex.cloud/ru/docs/storage/operations/buckets/create)
и настройке [публичного доступа](https://yandex.cloud/ru/docs/storage/operations/buckets/bucket-availability).

Устанавливаем в strapi плагин для работы с S3 хранилищем.

```
npm install @strapi/provider-upload-aws-s3 --save
```

Добавить конфигурацию для подключения к S3 Yandex cloud

```
module.exports = ({ env }) => ({
  upload: {
    config: {
      provider: 'aws-s3',
      providerOptions: {
        credentials: {
          accessKeyId: env('YC_ACCESS_KEY_ID'),
          secretAccessKey: env('YC_ACCESS_SECRET'),
        },
        region: 'ru-central1',
        endpoint: 'https://storage.yandexcloud.net',
        params: {
          Bucket: env('YC_BUCKET'),
        },
      },
    },
  },
});
```

Для отображения в галерее превью картинок необходимо добавить домен в доверенный.

```
{
    name: 'strapi::security',
    config: {
      contentSecurityPolicy: {
        useDefaults: true,
        directives: {
          'connect-src': ["'self'", 'https:'],
          'img-src': [
            "'self'",
            'data:',
            'blob:',
            'market-assets.strapi.io',
            'https://'+env('YC_BUCKET')+'.storage.yandexcloud.net',
          ],
          'media-src': [
            "'self'",
            'data:',
            'blob:',
            'market-assets.strapi.io',
            'https://'+env('YC_BUCKET')+'.storage.yandexcloud.net',
          ],
          upgradeInsecureRequests: null,
        },
      },
    },
  },
```

Создаем ключ и секрет для загрузки файлов в бакет.

1. [Создайте сервисный аккаунт](https://yandex.cloud/ru/docs/iam/operations/sa/create).
2. Назначьте сервисному аккаунту роль `storage.uploader`
3. [Создайте статический ключ доступа](https://yandex.cloud/ru/docs/iam/operations/sa/create-access-key).

Добавляем новые переменные окружения.

- `YC_BUCKET` - название бакета
- `YC_ACCESS_KEY_ID` - идентификатор ключа
- `YC_ACCESS_SECRET` - секретный ключ

Исходный код руководства на [GitHub](https://github.com/updevru/tutorial-strapi-deploy).