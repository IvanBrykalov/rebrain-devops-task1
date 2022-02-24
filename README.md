# **MyApplication (MyApp)**

> MyApp for sending messages to RabbitMQ

MyApp is a client application (producer) for RabbitMQ
Use MyApp for test sending messages to RabbitMQ.
MyApp is written in python.

![`Common scheme`](/images/scheme.jpeg)

## Requirements

To run this app you need to

1. install RabbitMQ. See [`RabbitMQ_docs`](https://www.rabbitmq.com/download.html)

2. install the `pika` package version `1.0.0` or later. To install it, run
```js
python -m pip install pika

```
You may first need to run
```js

easy_install pip
```

## Usage

run:

```js

python myapp
```

outputs:

```
[x] Sent 'Hello world!'
```

## API

Python code used `pika` library.
When using this library, work with RabbitMQ will consist of three main stages:

1. Setting up a connection
2. Performing the required operations
3. Closing the connection


to establish a connection with RabbitMQ, MyApp's code used this:
```js
connection = pika.BlockingConnection(
    pika.ConnectionParameters(host='localhost'))
channel = connection.channel()

channel.queue_declare(queue='hello')

```
to publish a massage, the method is used:
```js
channel.basic_publish(exchange='', routing_key='hello', body='Hello world!')
print(" [x] Sent 'Hello world!'")
```

to close connection:
```js
connection.close()
```

## Install

1. install the `pika` package version `1.0.0` or later. To install it, run
```js
python -m pip install pika

```
You may first need to run
```js

easy_install pip
```
2. download MyApp with `wget`:

```js
wget https://github.com/IvanBrykalov/Ivan-Brykalov/blob/master/test.md
```

or clone repo to you local project:

```js
git clone https://github.com/IvanBrykalov/Ivan-Brykalov.git
```

3. edit `myapp.py` to configure the connection to RabbitMQ by your text editor:
```js
vim myapp.py
```
4. grant execution rights to file `myapp.py`

```js
# chmod +x myapp.py
```

5. run `myapp.py` to send your message to RabbitMQ:

```js

python myapp
```
## Acknowledgments

MyApp isn't unique or single application for send messages to RabbitMQ.
But it's good for easy testing sending messages to RabbitMQ.
Thanks to Rebrainme for the excellent education and the materials supplied!

## See Also

- [`RabbitMQ Tutorials`](https://www.rabbitmq.com/getstarted.html)
- [`Habr article`](https://habr.com/ru/post/434510)
- [`Rebrainme`](https://rebrainme.com)

Other clients libraries and developer tools for python:

Num | Librarie | Description
----|:--------:|----:
| 1. | [`rstream`](https://github.com/qweeze/rstream) |  RabbitMQ Stream Python client |
| 2. | [`aio-pika`](https://github.com/mosquito/aio-pika) |  A pure-Python AMQP 0-9-1 client built for Python 3 and asyncio |
| 3. | [`Celery`](https://docs.celeryproject.org/en/latest/) |  A distributed task queue for Django and pure Python |




## License

ISC

