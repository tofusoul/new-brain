---
title: Rabbitmq
date: 2024-03-12
---

# Setup Notess

- this helped up to the amin panel, just needed to seup the user
    - https://computingforgeeks.com/installing-rabbitmq-on-centos-fedora/
- not what I actually used. but seems like the same steps:
    https://medium.com/analytics-vidhya/how-to-use-rabbitmq-with-python-e0ccfe7fa959

** Minimum Rabbit MQ Demo
```python
import pika

creds = pika.PlainCredentials("tofu", "f1zzl3p0p")
params = pika.ConnectionParameters("170.64.169.74", 5672, "/", creds)
connection = pika.BlockingConnection(params)
channel = connection.channel()
channel.queue_declare(queue="hello")
channel.basic_publish(exchange="", routing_key="hello", body="Hello World!")
print(" [x] Sent 'Hello World!'")
connection.close()
```
