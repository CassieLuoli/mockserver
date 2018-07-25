# mockserver


A standlone mockserver with some basic demo api already built-in. ** This a demo of mock server built with https://github.com/dreamhead/moco **

## How to run the mock server

```
./start.sh
```

## Built-in APIs

4 APIs are built-in this demo.

* Login
* getProfile
* getNews
* getNews with ID

You can use Postman to trigger the mock server. 

** Login **

```
post http://127.0.0.1:12306/user

body:
{
    "username": "valid",
    "passwrod": "valid"
}
```

Response 200 should be get:

```
{
    "auth": {
        "id-token": "123456",
        "access-token": "98908989089",
        "refresh-token": "34545234234"
    }
}
```

Please try to post some wrong username & password value to mock server. What you would get?

** getProfile **

```
get http://127.0.0.1:12306/user/profile

header:
   "id-token": "123456",
   "access-token": "98908989089"
```

Response 200 should be get:

```
{
    "profile": {
        "name": "John Smith",
        "gender": "male",
        "avartar": ""
    }
}
```

** getNews **

```
get http://127.0.0.1:12306/news

header:
   "id-token": "123456",
   "access-token": "98908989089"
```

Response 200 should be get:

```
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

** getNews With ID **

id doesn't have to to 123, can be any string.

```
get http://127.0.0.1:12306/news/123

header:
   "id-token": "123456",
   "access-token": "98908989089"
```

Response 200 should be get:

```
{
    "content": {
        "id": "123",
        "header": "",
        "content": {}
    }
}
```


