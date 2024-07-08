# Example usage

## How to connect to mongo server
```python
import pymongo

client = pymongo.MongoClient("mongodb://localhost:27017/")
db = client["mydatabase"]
```

## How to create collection
```python
import pymongo

client = pymongo.MongoClient("mongodb://localhost:27017/")
db = client["mydatabase"]
collection = db["customers"]
```

## How to insert data
```python
import pymongo

client = pymongo.MongoClient("mongodb://localhost:27017/")
db = client["mydatabase"]
collection = db["customers"]

data = {"name": "John", "address": "Highway 37"}
collection.insert_one(data)
```

## How to find data
```python
import pymongo

client = pymongo.MongoClient("mongodb://localhost:27017/")
db = client["mydatabase"]
collection = db["customers"]

for x in collection.find():
    print(x)
```

## How to query data
```python
import pymongo

client = pymongo.MongoClient("mongodb://localhost:27017/")
db = client["mydatabase"]
collection = db["customers"]

query = {"address": "Highway 37"}
result = collection.find(query)
for x in result:
    print(x)
```

## How to delete data
```python
import pymongo

client = pymongo.MongoClient("mongodb://localhost:27017/")
db = client["mydatabase"]
collection = db["customers"]

query = {"address": "Highway 37"}
collection.delete_one(query)
```

## How to update data
```python
import pymongo

client = pymongo.MongoClient("mongodb://localhost:27017/")
db = client["mydatabase"]
collection = db["customers"]

query = {"address": "Highway 37"}
new_values = {"$set": {"address": "Canyon 123"}}
collection.update_one(query, new_values)
```

## How to drop collection
```python
import pymongo

client = pymongo.MongoClient("mongodb://localhost:27017/")
db = client["mydatabase"]
collection = db["customers"]

collection.drop()
```

## How to drop database
```python
import pymongo

client = pymongo.MongoClient("mongodb://localhost:27017/")
client.drop_database("mydatabase")
```

## How to close connection
```python
import pymongo

client = pymongo.MongoClient("mongodb://localhost:27017/")
client.close()
```

## How to create index
```python
import pymongo

client = pymongo.MongoClient("mongodb://localhost:27017/")
db = client["mydatabase"]
collection = db["customers"]

collection.create_index("name")
```

## How to create unique index
```python
import pymongo

client = pymongo.MongoClient("mongodb://localhost:27017/")
db = client["mydatabase"]
collection = db["customers"]

collection.create_index("name", unique=True)
```

## How to create compound index
```python
import pymongo

client = pymongo.MongoClient("mongodb://localhost:27017/")
db = client["mydatabase"]
collection = db["customers"]

collection.create_index([("name", 1), ("address", -1)])
```

