# Intro avro
[Main site](https://avro.apache.org)

[Documentation](https://avro.apache.org/docs/1.11.1/getting-started-python/)

[Fastavro main site](https://github.com/fastavro/fastavro)

## How to install fastavro:
```bash
pip install fastavro
```

## Example usage

### How to read/write 
```python
import fastavro
schema = {
    "type": "record",
    "name": "example",
    "fields": [
        {"name": "name", "type": "string"},
        {"name": "age", "type": "int"},
        {"name": "city", "type": "string"}
    ]
}
# Writing data
with open('example.avro', 'wb') as out:
    fastavro.writer(out, schema, [
        {"name": "Alyssa", "age": 10, "city": "San Francisco"},
        {"name": "Ben", "age": 20, "city": "San Francisco"}
    ])
# Reading data
with open('example.avro', 'rb') as fo:
    reader = fastavro.reader(fo)
    for record in reader:
        print(record)
```

### How to load django model to avro and from avro

```python
import fastavro
from django.db import models


class Example(models.Model):
    name = models.CharField(max_length=100)
    age = models.IntegerField()
    city = models.CharField(max_length=100)

    @classmethod
    def avro_schema(cls):
        return {
            "type": "record",
            "name": "example",
            "fields": [
                {
                    "name": "name",
                    "type": "string"
                },
                {
                    "name": "age",
                    "type": "int"
                },
                {
                    "name": "city",
                    "type": "string"
                }
            ]
        }

    def to_avro(self):
        return {
            "name": self.name,
            "age": self.age,
            "city": self.city
        }

    @classmethod
    def from_avro(cls, data):
        return cls(
            name=data["name"],
            age=data["age"],
            city=data["city"]
        )

    class Meta:
        managed = False
        db_table = 'example'
        app_label = 'example'
        abstract = True
        verbose_name = 'Example'
        verbose_name_plural = 'Examples'
        ordering = ['name']

# Writing data
with open('example.avro', 'wb') as out:
    fastavro.writer(out, Example.avro_schema(), [
        Example(name="Alyssa", age=10, city="San Francisco").to_avro(),
        Example(name="Ben", age=20, city="San Francisco").to_avro()
    ])
# Reading data
with open('example.avro', 'rb') as fo:
    reader = fastavro.reader(fo)
    for record in reader:
        print(Example.from_avro(record))
```

### How to append data to exists avro file
```python
import fastavro

schema = {
    "type": "record",
    "name": "example",
    "fields": [
        {"name": "name", "type": "string"},
        {"name": "age", "type": "int"},
        {"name": "city", "type": "string"}
    ]
}
# Writing data
with open('example.avro', 'ab+') as out:
    fastavro.writer(out, schema, [
        {"name": "Alyssa", "age": 10, "city": "San Francisco"},
        {"name": "Ben", "age": 20, "city": "San Francisco"}
    ])
# Reading data
with open('example.avro', 'rb') as fo:
    reader = fastavro.reader(fo)
    for record in reader:
        print(record)
```





