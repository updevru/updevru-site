---
title: "Мое резюме"
type: page
showTableOfContents: true
---

Меня зовут Ладыгин Сергей, я профессионально занимаюсь разработкой более 15 лет. Муж и отец 3 детей.
Увлекаюсь спортом - велосипед, плавание, баскетбол, волейбол, настольный тенис. 

## Компетенции

### 1. Программирование

Мои основные языки программирование - **PHP** и **JavaScript**. В них я лучше всего разбираюсь и дольше всего с ними работаю.
В этом стэке много работал с фреймворками **Symfony** и Laravel.

Последнее время в основном программирую на **TypeScript**, **Go** и **Node**.

Знаю базы данных **PostgreSQL**, **MySQL** и **MongoDB** на хорошем уровне (оптимизация, хранимые процедуры, условные индексы и прочее).

Умею работать с очередями сообщения (**RabbitMQ**, **Kafka**) для интеграции между сервисами и для фоновых задач.

### 2. Проектирование систем

Большой опыт проектирования маленьких и больших веб приложений. 
Разбираюсь как и на какие сервисы лучше разбить приложение, как настроить между ними надежную интеграцию, 
как приложение эффективно разместить в одном или нескольких дата центрах.

**Есть опыт проектирования**: соц. сетей, интернет-магазинов, медиа-порталов, crm систем, образовательных порталов, конструкторов сайтов.

### 3. Управление командой разработки

Прошел путь от рядового разработчика до тимлида, знаю и применяю методики **Scrum** и **Kanban**.

Опыт построения процесса разработки в разных командах полностью с нуля по этапам:

Постановка задачи -> Оценка -> Планирование -> Разработка -> Проверка кода -> Тестирование -> Выкладка.

Могу не только выстроить организационно, но и реализовать все технические моменты от настройки **Jira** (или другой софт) до настройки **CI/CD** для сборки и выкладки.

Самая большая мой команда состояла из **13 человек** (6 разработчиков, 2 тестировщика, 3 аналитика, 2 администратора).

### 4. DevOps

Могу не только спроектировать и разработать систему, но и наладить процесс выкладки и настроить сервера.

Знаю **Linux (Ubuntu, Debian)** на уровне администратора, большой опыт применения **Ansible** для настройки серверов.
Умею упаковывать приложения в **Docker** и запускать контейнеры в кластере на **Docker swarm**.

Опыт настройки: **Nginx**, **Apache**, **Traefik**, **PHP-FPM**, **ELK**, **MySQL**.

Знание CI/CD: **TeamCity**, **Bitbucket Pipelines**, **Github Actions**.

## Карьера

### Finam.ru

Москва **•** Финансовый сектор **•** Май 2011 — по настоящее время

Должность: **Ведущий программист позже тимлид**

В компании я занимался разными проектами: социальная сеть для трейдеров, crm система, портал дистанционного обучения и
конструктор сайтов. Ниже о каждом из них более подробно.

#### 1) Социальная сеть для трейдеров

Май 2011 - Январь 2011.

Стэк: PHP 5, PostgreSQL, самописный движок, jQuery, PGQ (система очередей на PostgreSQL), SonicMQ (коммерческая система очередей).

Занимался разработкой нового функционала и доработкой существующего. Научился проектировать системы с расчетом
на высокую нагрузку и на большие объемы данных. Познакомился с очередями для фоновых задач.

#### 2) CRM система

Январь 2011 - Август 2021.

Стэк: PHP 5 - 8, Zend Framework, Symfony 3 - 5, PostgreSQL, MongoDB, Elasticsearch, jQuery, ReactJS, PGQ, SonicMQ, Kafka, WebRTC.

Занимался проектированием и разработкой crm системы с нуля под требования бизнеса. Прошел путь от разработчика до тимлида с командой в 13 человек.
Система обслуживает несколько международных бизнесов, несколько call центров численностью более 400 операторов каждый. 
Функционал CRM покрывает полностью все процессы, от приема заявок, поддержка, открытия и ведение клиентов.

Функционал:
- прием заявок и распределение на сотрудников
- интеграция с телефонией
- интеграция с электронной очередью
- интеграция с почтовыми ящиками по imap для приема писем и ответа на них
- агрегация полной информации о клиентах из разных внутренних сервисов
- интеграция с торговыми системами
- учет продаж продуктов компании
- отчетность для руководителей всех уровней
- возможность звонить из браузера (web phone по WebRTC)
- и многое другое.

Первая версия системы была написана на Zend framework и MongoDB (выбор был неудачным для crm). 
Из-за проблем с целостностью данных и сложностями при построении отчетов было решено заменить MongoDB на PostgreSQL.
Рефакторинг и переход на новую БД занял чуть больше 1 года (в итоге получилось более 100 таблиц), переход был осуществлен без простоя.

Позже было решено переходить с Zend framework 1 на Symfony в связи с остановкой поддержки первого. 
Определили целевой стек Symfony, API Platform, EasyAdmin, ReactJS, Ant Design. Цель достигнута.

#### 3) Портал дистанционного обучения

Август 2021 - текущее время.

Стэк: PHP8, Laravel, PostgreSQL, Kafka, Docker, Minio.

Собрал новую команду для реализации сервиса дистанционного обучения. Занимался проектированием, разработкой, взаимодействием с подрядчиком.

Навел порядок в проете после подрядчика, настроил работу приложения в Docker, реализовал CI/CD, написал техническую документацию.

#### 4) Конструктор сайтов

Сентябрь 2022 - текущее время.

Стэк: Node, Next.js, Strapi, GrapesJS, Go, PostgreSQL, Kafka, Docker.

Собрал новую команду, спроектировал архитектуру конструктора сайтов с учетом высокой нагрузки.
Главное требование к системе - создание лендингов без привлечения разработчиков и высокая скорость работы.

Реализовал архитектуру в виде микро-сервисов, перешел на другой стэк TypeScript и Go. 

### Pichesky

Москва **•** Рекламное агентство **•** Декабрь 2009 — май 2011

Должность: **PHP программист**

В мои обязанности входило:
- Проектирование веб-проектов
- Проектирование баз данных
- Программирование и запуск веб-проектов

Работа с высокими нагрузками и постоянно меняющимися требованиями к проекту. 
Глубокие знания Zend Framwork, PostgreSql, Memcached, MySQL, проектирование систем управления.

### Cafemam.ru

Псков **•** Интернет-портал **•** Декабрь 2008 — декабрь 2009

Должность: **PHP-программист**

В обязанности входило разработка нового, улучшение существующего функционала и исправление ошибок.

За время работы я приобрёл опыт работы в команде, навыки работы с SVN и багтрекером. 
А так же более глубокие знания PHP, MySQL, JavaScript, XML и основы оптимизации баз данных. 
Изучение объектно-ориентированного программирования и основ UML. 
Проектирование и разработка системы управления на базе фреймворка CodeIgniter. 
Изучение UNIX (Ubuntu).