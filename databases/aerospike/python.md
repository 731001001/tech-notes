# Python aerospike

## Docs

- [Aerospike Python client](https://www.aerospike.com/docs/client/python/index.html)

## How to install python aerospike

```bash
pip install aerospike
```

## CRUD python aerospike

```python
# Import Aerospike client libraries
import aerospike
from aerospike import GeoJSON
from aerospike import exception as ex
from aerospike_helpers.operations import operations as op_helpers
from aerospike_helpers.operations import map_operations

# This is for formatting out in the sandbox
import pprint

# ***
# Setup
# ***

address = "127.0.0.1"   # Aerospike address
port = 3000             # Aerospike port
namespace = "test"      # Cluster namespace
setname = "foo"         # Set name within namespace

# Create the client and connect to the database
client = aerospike.client({'hosts': [(address, port)]})

# ***
# Write a record
# ***

# Create a new write policy
write_policy = {'total_timeout': 5000}

# Create the record key
# A tuple consisting of namespace, set name, and user defined key
key = (namespace, setname, "bar")

# Create a bin to store data within the new record
bins = {'myBin': 'Hello World!'}

# Write the record to your database
try:
    client.put(key, bins, policy=write_policy)
    print("Successfully wrote record")
except ex.AerospikeError as e:
    print(e)

# ***
# Read back the record we just wrote
# ***

# Create a new read policy
read_policy = {'total_timeout': 5000}

# Read the record
try:
    (key_, meta, bins) = client.get(key, policy=read_policy)
    print(bins)
except ex.AerospikeError as e:
    print(e)


try:
    client.put(key, {'myBin': 'test'}, policy=write_policy)
    (key, meta, bins) = client.select(key,['myBin'])
    print('Update succeeded\nKey:', key[2], '\nBin:', bins)
except ex.AerospikeError as e:
    print("Update failed\nError: {0} [{1}]".format(e.msg, e.code))

remove_policy = {'total_timeout': 5000}

try:
    client.remove(key, policy=remove_policy)
    print('Record deleted')

    # Check if record exists
    (key, meta) = client.exists(key)
    exists = True
    if meta == None:
        exists = False
    print('Record exists: ', exists)
except ex.AerospikeError as e:
    print("Delete failed\nError: {0} [{1}]".format(e.msg, e.code))
    print(e)
finally:
    # Close the client
    client.close()
```



