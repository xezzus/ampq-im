# Мгновенные сообщения через AMQP

## Установка

Для работы с компонентом требуется установить библиотеку AMQP через PECL

[pecl amqp](https://pecl.php.net/package/amqp/1.6.0beta2)

## Использование

```
// подклimючение к точке обмена сообщениями
$im = Yii::$app->exchange('globalChat');

// Отправить сообщение в точку обмена
$im->send('Text message');

// Получить сообщение
$take = $im->take();

// Получить тело сообщения
$take->msg();

// Сообщение серверу, что сообщение обработано и его можно удалить из очереди
$take->ack();
```

## Конфигурация

```
"components"=>[
  "im"=>[
    'class' => 'common\components\im\Connection',
    'host'=>'127.0.0.1',
    'login'=>'guest',
    'password'=>'guest',
    'port'=>'5672'
  ]
]
```
