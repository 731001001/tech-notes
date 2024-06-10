# Lua using in redis

## example 1
```python
import redis

client = redis.Redis(host='localhost', port=6379, decode_responses=True)

example_data = [{
                "score": 10,
                "country": "US",
                "test_value": 10344
                },
                {
                "score": 20,
                "country": "US",
                "test_value": 10344
                },
                {
                "score": 30,
                "country": "US",
                "test_value": 10344
                }]
client.json().set('example_data', '$', example_data)

# Lua script to sum imp_weight
lua_script = """
local data = redis.call('JSON.GET', KEYS[1])
local total = 0

if data then
    local json = cjson.decode(data)
    for _, item in ipairs(json) do
        if item.country == "US" and item.test_value == 10344 then
            total = total + item.score
        end
    end
end

return total
"""

# Load the Lua script into Redis
lua_sha = client.script_load(lua_script)

# Execute the Lua script
key = 'example_data'
result = client.evalsha(lua_sha, 1, key)
print(f'Total score: {result}')
```