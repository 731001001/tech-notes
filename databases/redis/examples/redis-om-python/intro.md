# Intro redis-om-python

[Main site](https://github.com/redis/redis-om-python)

[Documentation](https://github.com/redis/redis-om-python/blob/main/docs/index.md)

## How to install redis-om-python:

```bash
pip install redis-om
```

## How to create model:

```python
from redis_om import Model, Field

class User(Model):
    name = Field()
    age = Field()
```

## How to create instance of model:

```python
from redis_om import Model, Field

class User(Model):
    name = Field()
    age = Field()

user = User(name="John", age=30)
```

## How to save instance to redis:

```python
from redis_om import Model, Field

class User(Model):
    name = Field()
    age = Field()

user = User(name="John", age=30)

user.save()
```

## How to get instance from redis:

```python
from redis_om import Model, Field

class User(Model):
    name = Field()
    age = Field()

user = User(name="John", age=30)
user.save()

user = User.get(user.id)
```

## How to update instance:

```python
from redis_om import Model, Field

class User(Model):
    name = Field()
    age = Field()

user = User(name="John", age=30)
user.save()
user.name = "Mike"
user.save()
```

## How to delete instance:

```python
from redis_om import Model, Field

class User(Model):
    name = Field()
    age = Field()

user = User(name="John", age=30)
user.save()
user.delete()
```

## How to find instances by pattern:

```python
from redis_om import Model, Field

class User(Model):
    name = Field()
    age = Field()

user = User(name="John", age=30)
user.save()
users = User.find("name:*")
```