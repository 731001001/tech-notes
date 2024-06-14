# Intro redis-py

[Main site](https://github.com/redis/redis-py)

[Documentation](https://redis-py.readthedocs.io/en/stable/)

## How to install redis-py:

```bash
pip install redis
```

## How to connect to redis server:

```python
import redis

r = redis.Redis(decode_responses=True)
```

## How to set key-value:

```python
import redis

r = redis.Redis(decode_responses=True)

res1 = r.set("key", "value")
print(res1)  # >>> True
```

## How to get value by key:

```python
import redis

r = redis.Redis(decode_responses=True)

res2 = r.get("key")
print(res2)  # >>> value
```

## How to delete key:

```python
import redis

r = redis.Redis(decode_responses=True)

res3 = r.delete("key")
print(res3)  # >>> 1
```

## How to make search by pattern:
```python
import redis

r = redis.Redis(decode_responses=True)

res4 = r.keys("k*")
print(res4)  # >>> ['key']
```

## How to make search values by pattern:
```python
import redis

r = redis.Redis(decode_responses=True)

res5 = r.mget("key1", "key2")
print(res5)  # >>> ['value1', 'value2']
```

## How to search values by pattern in deep json:
```python
import redis

r = redis.Redis(decode_responses=True)

res6 = r.json().get("key", "$.key1")
print(res6)  # >>> ['value1']
```

## How to set value in deep json:
```python
import redis

r = redis.Redis(decode_responses=True)

res7 = r.json().set("key", "$.key1", "value1")
print(res7)  # >>> True
```
