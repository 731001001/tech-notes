# pymongo Errors

## ExceededMemoryLimit

### error
```text
pymongo.errors.OperationFailure: $push used too much memory and cannot spill to disk. Memory limit: 104857600 bytes, full error: {'ok': 0.0, 'errmsg': '$push used too much memory and cannot spill to disk. Memory limit: 104857600 bytes', 'code': 146, 'codeName': 'ExceededMemoryLimit'}
```

### solution
use allowDiskUse=True, but in new mongo server versions, doesn't work.