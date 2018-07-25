# mockserver

**This a demo of mock server built with https://github.com/dreamhead/moco** 

A standlone mockserver with some basic demo api already built-in. 



## How to run the mock server

```
./start.sh
```



## Built-in APIs

4 APIs are built-in this demo. You can add more to match your business value.

* Login
* getProfile
* getNews
* getNews with ID



You can use Postman to trigger the mock server. 



**Login**

```Json
post http://127.0.0.1:12306/user/login

body:
{
    "username": "valid",
    "password": "valid"
}
```

Response 200 should be get:

```Json
{
    "auth": {
        "id-token": "123456",
        "access-token": "98908989089",
        "refresh-token": "34545234234"
    }
}
```

Please try to post some wrong username & password value to mock server. What you would get?

**getProfile**

```json
get http://127.0.0.1:12306/user/profile

header:
   "id-token": "123456",
   "access-token": "98908989089"
```

Response 200 should be get:

```Json
{
    "profile": {
        "name": "John Smith",
        "gender": "male",
        "avartar": ""
    }
}
```

**getNews**

```Json
get http://127.0.0.1:12306/news

header:
   "id-token": "123456",
   "access-token": "98908989089"
```

Response 200 should be get:

```Json
{
    "timestamp": 123123123,
    "news": [
        {
            "id": "123",
            "title": "Tomorrow would rain",
            "subtitle": "Tomorrow would rainTomorrow would rainTomorrow would rainTomorrow would rain"
        },
        ...
    ]
}
```

If neither id-token | access-token is given with right value. 400 should be returned.



**getNews With ID**

ID doesn't have to to 123, can be any string.

```json
get http://127.0.0.1:12306/news/123

header:
   "id-token": "123456",
   "access-token": "98908989089"
```

Response 200 should be get:

```Json
{
    "content": {
        "id": "123",
        "header": "",
        "content": {}
    }
}
```


