# Aerospike intro

## Docs

- [Aerospike](https://www.aerospike.com/docs/)
- [Aerospike Python client](https://www.aerospike.com/docs/client/python/index.html)
- [Aerospike Python client API reference](https://www.aerospike.com/apidocs/python/)
- [Aerospike devs](https://aerospike.com/developer/)

## How to install aerospike

- [Install aerospike](https://www.aerospike.com/docs/operations/install/)

### How to install ubuntu

```bash
wget -O aerospike.tgz https://download.aerospike.com/artifacts/aerospike-server-community/7.1.0/aerospike-server-community_7.1.0.2_tools-11.0.1_ubuntu20.04_x86_64.tgz
tar -xvf aerospike.tgz
cd aerospike-server-community_7.1.0.2_tools-11.0.1_ubuntu20.04_x86_64
sudo ./asinstall
sudo systemctl start aerospike
```

### How to verify installation

- [Verify installation](https://www.aerospike.com/docs/operations/install/verify.html)

```bash
aql -h 127.0.0.1 -c "INSERT INTO test.demo (PK, name, address, email) VALUES ('Aerospike', 'Aerospike, Inc.', 'Mountain View, CA 94043', 'info@aerospike.com')"
```

```bash
aql -h 127.0.0.1 -c "select * from test.demo where PK='Aerospike'"
```

```bash
aql -h 127.0.0.1 -c "DELETE FROM test.demo where PK='Aerospike'"
```



