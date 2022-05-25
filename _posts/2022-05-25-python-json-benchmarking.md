---
 title: Benchmarking Python JSON serializers - json vs ujson vs orjson  
 tags: [python, json, benchmarking]
 style: fill
 color: light
 excerpt: If you work with a large datasets in json inside your python code, then you might want to try using 3rd party libraries like ujson and orjson
 comments: true
 categories: computer-science
 last_modified_at: 2022-05-25T22:40:00+05:30
---
## Introduction
If you work with a large datasets in json inside your python code, 
then you might want to try using 3rd party libraries like [ujson](https://github.com/ultrajson/ultrajson)
and [orjson](https://github.com/ijl/orjson) 
which are replacements to python's json library. 

As per their documentation
- [ujson](https://github.com/ultrajson/ultrajson) (UltraJSON) is an ultra fast JSON encoder and decoder written in pure C with bindings for Python 3.7+.

- [orjson](https://github.com/ijl/orjson) is a fast, correct JSON library for Python. It is the fastest python library for json encoding & decoding. It serializes dataclass, datetime, numpy, and UUID instances natively.


## Benchmarking
I did a basic benchmark comparing json, ujson and orjson. 
The benchmarking results were interesting.

```python
import time
import json
import orjson
import ujson


def benchmark(name, dumps, loads):
    start = time.time()
    for i in range(3000000):
        result = dumps(m)
        loads(result)
    print(name, time.time() - start)


if __name__ == "__main__":
    m = {
        "timestamp": 1556283673.1523004,
        "task_uuid": "0ed1a1c3-050c-4fb9-9426-a7e72d0acfc7",
        "task_level": [1, 2, 1],
        "action_status": "started",
        "action_type": "main",
        "key": "value",
        "another_key": 123,
        "and_another": ["a", "b"],
    }

    benchmark("Python", json.dumps, json.loads)
    benchmark("ujson", ujson.dumps, ujson.loads)

    # orjson only outputs bytes, but often we need unicode:
    benchmark("orjson", lambda s: str(orjson.dumps(s), "utf-8"), orjson.loads)

# OUTPUT:
# Python 12.502133846282959
# ujson 4.428200960159302
# orjson 2.3136467933654785
```
> [ujson](https://github.com/ultrajson/ultrajson) is 3 times faster than the standard json library

> [orjson](https://github.com/ijl/orjson) is over 6 times faster than the standard json library


## Conclusion

For most cases, you would want to go with python's standard json library which removes
dependencies on other libraries. On other hand you could try out [ujson](https://github.com/ultrajson/ultrajson)
which is simple replacement for python's json library. If you want more speed and also want 
dataclass, datetime, numpy, and UUID instances and you are ready to deal with more complex code,
then you can try your hands on [orjson](https://github.com/ijl/orjson)


