# Intro mongo
[Main site](https://www.mongodb.com/)

[Documentation](https://docs.mongodb.com/manual/)

[Configuration](https://docs.mongodb.com/manual/reference/configuration-options/)

[PyMongo Documentation](https://pymongo.readthedocs.io/en/stable/)

## How to install mongo to ubuntu server:
```bash
sudo apt-get install mongodb
```

### How to start mongo server:
```bash
sudo systemctl start mongodb
```
or
```bash
mongod --fork --logpath /var/log/mongodb/mongodb.log --dbpath /var/lib/mongodb
```

### How to restart mongo server:
```bash
sudo systemctl restart mongodb
```
or
```bash
mongod --dbpath /var/lib/mongodb --shutdown && mongod --fork --logpath /var/log/mongodb/mongodb.log --dbpath /var/lib/mongodb
```

## How to install pymongo:
```bash
pip install pymongo
```

## How to open port 27017:
```bash
sudo ufw allow 27017
```









