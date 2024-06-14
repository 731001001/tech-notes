# pymongo Errors

## ExceededMemoryLimit

### error
```text
pymongo.errors.OperationFailure: $push used too much memory and cannot spill to disk. Memory limit: 104857600 bytes, full error: {'ok': 0.0, 'errmsg': '$push used too much memory and cannot spill to disk. Memory limit: 104857600 bytes', 'code': 146, 'codeName': 'ExceededMemoryLimit'}
```

### solution
use allowDiskUse=True, but in new mongo server versions, doesn't work.

## ServerSelectionTimeoutError

### error
```text
pymongo.errors.ServerSelectionTimeoutError: <server>:27017: [Errno 111] Connection refused
```

### solution
#### check if mongo server is running
```bash
sudo systemctl status mongodb
```

#### check if mongo server is listening on port 27017
```bash
sudo netstat -tulnp | grep 27017
```

#### check telnet port 27017 on client side
```bash
telnet <server> 27017
```