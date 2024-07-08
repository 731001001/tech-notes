# Intro redis
[Main site](https://redis.io)
[Redis Documentation](https://redis.io/documentation)

## How to install on the redis json server:
https://redis.io/docs/latest/operate/oss_and_stack/install/install-stack/linux/

```bash
curl -fsSL https://packages.redis.io/gpg | sudo gpg --dearmor -o /usr/share/keyrings/redis-archive-keyring.gpg
sudo chmod 644 /usr/share/keyrings/redis-archive-keyring.gpg
echo "deb [signed-by=/usr/share/keyrings/redis-archive-keyring.gpg] https://packages.redis.io/deb $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/redis.list
sudo apt-get update
sudo apt-get install redis-stack-server
```

### how to start redis server:
```bash
sudo systemctl start redis-stack-server
```

## Redis json with python:
[docs](https://redis.readthedocs.io/en/stable/examples.html)

### How to install redis-py
```bash
pip install redis
```

### Mini example json path:
[docs](https://redis.io/docs/latest/develop/data-types/json/path/)
```python
"""
Code samples for JSON doc pages: https://redis.io/docs/latest/develop/data-types/json/
"""
import redis

r = redis.Redis(decode_responses=True)

res1 = r.json().set("bike", "$", '"Hyperion"')
print(res1)  # >>> True

res2 = r.json().get("bike", "$")
print(res2)  # >>> ['"Hyperion"']

res3 = r.json().type("bike", "$")
print(res3)  # >>> ['string']


res4 = r.json().strlen("bike", "$")
print(res4)  # >>> [10]

res5 = r.json().strappend("bike", '" (Enduro bikes)"')
print(res5)  # >>> 27

res6 = r.json().get("bike", "$")
print(res6)  # >>> ['"Hyperion"" (Enduro bikes)"']


res7 = r.json().set("crashes", "$", 0)
print(res7)  # >>> True

res8 = r.json().numincrby("crashes", "$", 1)
print(res8)  # >>> [1]

res9 = r.json().numincrby("crashes", "$", 1.5)
print(res9)  # >>> [2.5]

res10 = r.json().numincrby("crashes", "$", -0.75)
print(res10)  # >>> [1.75]


res11 = r.json().set("newbike", "$", ["Deimos", {"crashes": 0}, None])
print(res11)  # >>> True

res12 = r.json().get("newbike", "$")
print(res12)  # >>> ['["Deimos", { "crashes": 0 }, null]']

res13 = r.json().get("newbike", "$[1].crashes")
print(res13)  # >>> ['0']

res14 = r.json().delete("newbike", "$.[-1]")
print(res14)  # >>> [1]

res15 = r.json().get("newbike", "$")
print(res15)  # >>> [['Deimos', {'crashes': 0}]]


res16 = r.json().set("riders", "$", [])
print(res16)  # >>> True

res17 = r.json().arrappend("riders", "$", "Norem")
print(res17)  # >>> [1]

res18 = r.json().get("riders", "$")
print(res18)  # >>> [['Norem']]

res19 = r.json().arrinsert("riders", "$", 1, "Prickett", "Royce", "Castilla")
print(res19)  # >>> [4]

res20 = r.json().get("riders", "$")
print(res20)  # >>> [['Norem', 'Prickett', 'Royce', 'Castilla']]

res21 = r.json().arrtrim("riders", "$", 1, 1)
print(res21)  # >>> [1]

res22 = r.json().get("riders", "$")
print(res22)  # >>> [['Prickett']]

res23 = r.json().arrpop("riders", "$")
print(res23)  # >>> ['"Prickett"']

res24 = r.json().arrpop("riders", "$")
print(res24)  # >>> [None]


res25 = r.json().set(
    "bike:1", "$", {"model": "Deimos", "brand": "Ergonom", "price": 4972}
)
print(res25)  # >>> True

res26 = r.json().objlen("bike:1", "$")
print(res26)  # >>> [3]

res27 = r.json().objkeys("bike:1", "$")
print(res27)  # >>> [['model', 'brand', 'price']]


inventory_json = {
    "inventory": {
        "mountain_bikes": [
            {
                "id": "bike:1",
                "model": "Phoebe",
                "description": "This is a mid-travel trail slayer that is a fantastic "
                "daily driver or one bike quiver. The Shimano Claris 8-speed groupset "
                "gives plenty of gear range to tackle hills and there\u2019s room for "
                "mudguards and a rack too.  This is the bike for the rider who wants "
                "trail manners with low fuss ownership.",
                "price": 1920,
                "specs": {"material": "carbon", "weight": 13.1},
                "colors": ["black", "silver"],
            },
            {
                "id": "bike:2",
                "model": "Quaoar",
                "description": "Redesigned for the 2020 model year, this bike "
                "impressed our testers and is the best all-around trail bike we've "
                "ever tested. The Shimano gear system effectively does away with an "
                "external cassette, so is super low maintenance in terms of wear "
                "and tear. All in all it's an impressive package for the price, "
                "making it very competitive.",
                "price": 2072,
                "specs": {"material": "aluminium", "weight": 7.9},
                "colors": ["black", "white"],
            },
            {
                "id": "bike:3",
                "model": "Weywot",
                "description": "This bike gives kids aged six years and older "
                "a durable and uberlight mountain bike for their first experience "
                "on tracks and easy cruising through forests and fields. A set of "
                "powerful Shimano hydraulic disc brakes provide ample stopping "
                "ability. If you're after a budget option, this is one of the best "
                "bikes you could get.",
                "price": 3264,
                "specs": {"material": "alloy", "weight": 13.8},
            },
        ],
        "commuter_bikes": [
            {
                "id": "bike:4",
                "model": "Salacia",
                "description": "This bike is a great option for anyone who just "
                "wants a bike to get about on With a slick-shifting Claris gears "
                "from Shimano\u2019s, this is a bike which doesn\u2019t break the "
                "bank and delivers craved performance.  It\u2019s for the rider "
                "who wants both efficiency and capability.",
                "price": 1475,
                "specs": {"material": "aluminium", "weight": 16.6},
                "colors": ["black", "silver"],
            },
            {
                "id": "bike:5",
                "model": "Mimas",
                "description": "A real joy to ride, this bike got very high "
                "scores in last years Bike of the year report. The carefully "
                "crafted 50-34 tooth chainset and 11-32 tooth cassette give an "
                "easy-on-the-legs bottom gear for climbing, and the high-quality "
                "Vittoria Zaffiro tires give balance and grip.It includes "
                "a low-step frame , our memory foam seat, bump-resistant shocks and "
                "conveniently placed thumb throttle. Put it all together and you "
                "get a bike that helps redefine what can be done for this price.",
                "price": 3941,
                "specs": {"material": "alloy", "weight": 11.6},
            },
        ],
    }
}

res1 = r.json().set("bikes:inventory", "$", inventory_json)
print(res1)  # >>> True

res2 = r.json().get("bikes:inventory", "$.inventory.*")
print(res2)
# >>>    [[{'id': 'bike:1', 'model': 'Phoebe',
# >>>       'description': 'This is a mid-travel trail slayer...

res3 = r.json().get("bikes:inventory", "$.inventory.mountain_bikes[*].model")
print(res3)  # >>> [['Phoebe', 'Quaoar', 'Weywot']]

res4 = r.json().get("bikes:inventory", '$.inventory["mountain_bikes"][*].model')
print(res4)  # >>> [['Phoebe', 'Quaoar', 'Weywot']]

res5 = r.json().get("bikes:inventory", "$..mountain_bikes[*].model")
print(res5)  # >>> [['Phoebe', 'Quaoar', 'Weywot']]


res6 = r.json().get("bikes:inventory", "$..model")
print(res6)  # >>> [['Phoebe', 'Quaoar', 'Weywot', 'Salacia', 'Mimas']]


res7 = r.json().get("bikes:inventory", "$..mountain_bikes[0:2].model")
print(res7)  # >>> [['Phoebe', 'Quaoar']]


res8 = r.json().get(
    "bikes:inventory",
    "$..mountain_bikes[?(@.price < 3000 && @.specs.weight < 10)]",
)
print(res8)
# >>> [{'id': 'bike:2', 'model': 'Quaoar',
#           'description': "Redesigned for the 2020 model year...


#  names of bikes made from an alloy
res9 = r.json().get(
    "bikes:inventory", "$..[?(@.specs.material == 'alloy')].model"
)
print(res9)  # >>> ['Weywot', 'Mimas']


res10 = r.json().get(
    "bikes:inventory", "$..[?(@.specs.material =~ '(?i)al')].model"
)
print(res10)  # >>> ['Quaoar', 'Weywot', 'Salacia', 'Mimas']


res11 = r.json().set(
    "bikes:inventory", "$.inventory.mountain_bikes[0].regex_pat", "(?i)al"
)
res12 = r.json().set(
    "bikes:inventory", "$.inventory.mountain_bikes[1].regex_pat", "(?i)al"
)
res13 = r.json().set(
    "bikes:inventory", "$.inventory.mountain_bikes[2].regex_pat", "(?i)al"
)

res14 = r.json().get(
    "bikes:inventory",
    "$.inventory.mountain_bikes[?(@.specs.material =~ @.regex_pat)].model",
)
print(res14)  # >>> ['Quaoar', 'Weywot']


res15 = r.json().get("bikes:inventory", "$..price")
print(res15)  # >>> [1920, 2072, 3264, 1475, 3941]

res16 = r.json().numincrby("bikes:inventory", "$..price", -100)
print(res16)  # >>> [1820, 1972, 3164, 1375, 3841]

res17 = r.json().numincrby("bikes:inventory", "$..price", 100)
print(res17)  # >>> [1920, 2072, 3264, 1475, 3941]


res18 = r.json().set(
    "bikes:inventory", "$.inventory.*[?(@.price<2000)].price", 1500
)
res19 = r.json().get("bikes:inventory", "$..price")
print(res19)  # >>> [1500, 2072, 3264, 1500, 3941]


res20 = r.json().arrappend(
    "bikes:inventory", "$.inventory.*[?(@.price<2000)].colors", "pink"
)
print(res20)  # >>> [3, 3]

res21 = r.json().get("bikes:inventory", "$..[*].colors")
print(
    res21
)  # >>> [['black', 'silver', 'pink'], ['black', 'white'], ['black', 'silver', 'pink']]
```

### Mini example json aggs:
[docs](https://redis.io/docs/latest/develop/data-types/json/aggs/)
```python
"""