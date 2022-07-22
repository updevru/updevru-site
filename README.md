# Исходник сайта updev.ru

Сайт построен на [CMS Hugo](https://gohugo.io/).

За основу взят шаблон [Gokarna](https://github.com/526avijitgupta/gokarna)

Запуск сайта для локальной разработки:

```bash
docker run -it --rm -p 1313:1313 -v $(pwd):/src --entrypoint bash -u $(id -u ${USER}):$(id -g ${USER}) klakegg/hugo:ubuntu
```

Сайт будет доступен по адресу [http://localhost:1313]