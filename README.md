# Исходник сайта updev.ru

Сайт построен на [CMS Hugo](https://gohugo.io/).

За основу взят шаблон [Gokarna](https://github.com/526avijitgupta/gokarna)

### Запуск сайта для локальной разработки:

Linux:

```bash
docker run -it --rm -p 1313:1313 -v $(pwd):/src -u $(id -u ${USER}):$(id -g ${USER}) klakegg/hugo:ubuntu server
```

Windows:

```bash
docker run -it --rm -p 1313:1313 -v ${PWD}:/src klakegg/hugo:ubuntu server
```

Сайт будет доступен по адресу [http://localhost:1313](http://localhost:1313)

### Тех. радар

Для построения радара используется скрипт https://github.com/zalando/tech-radar