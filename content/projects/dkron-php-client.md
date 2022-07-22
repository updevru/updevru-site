---
title: Dkron PHP Client
type: page
showTableOfContents: true
---

Клиент на PHP для API [Dkron](https://dkron.io). 

Бибилиотека использует последнюю версию API, работает на актуальных версиях PHP и 100% кода покрыто unit тестами.

[Документация API Dkron](https://dkron.io/api/)

### Пример подключения библиотеки в проект

```bash
composer require updevru/dkron-php-client
```

### Пример использования
```php
use Http\Client\Curl\Client;
use Nyholm\Psr7\Factory\Psr17Factory;
use Updevru\Dkron\ApiClient;
use Updevru\Dkron\Endpoint\EndpointCollection;

$client = new Updevru\Dkron\ApiClient(
    new Updevru\Dkron\Endpoint\EndpointCollection(
        [
            [
                'url' => 'http://localhost',
                'login' => null,
                'password' => null,
            ]
        ]
    ),
    new Http\Client\Curl\Client(),
    new Nyholm\Psr7\Factory\Psr17Factory(),
    new Nyholm\Psr7\Factory\Psr17Factory()
);

$api = new \Updevru\Dkron\Api($client, new \Updevru\Dkron\Serializer\JMSSerializer());

$jobs = $api->jobs->getJobs();

$newJob = new \Updevru\Dkron\Dto\JobDto();
$newJob->setName('test_job');
$newJob->setSchedule('*/2 * * * * *');
$newJob->setConcurrency(\Updevru\Dkron\Dto\JobDto::CONCURRENCY_FORBID);
$newJob->setExecutor('shell');
$newJob->setExecutorConfig(['command' => 'echo Hello']);

$api->jobs->createOrUpdateJob($newJob);

$api->jobs->toggleJob('test_job');
$api->jobs->deleteJob('test_job');
```

Более подробная информация на [Github](https://github.com/updevru/dkron-php-client).