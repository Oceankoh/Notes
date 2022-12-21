## Description

Applies a coupon to a specified basket. 

## Connection Details

HTTP Methods: `PUT`
Parameters: 
- `<id>`

### Sample Request

```http
PUT /rest/basket/6/coupon/l%7D6D%23ga%2Bjm HTTP/1.1
Host: localhost:3000
User-Agent: Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:108.0) Gecko/20100101 Firefox/108.0
Accept: application/json, text/plain, */*
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Referer: http://localhost:3000/
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJzdGF0dXMiOiJzdWNjZXNzIiwiZGF0YSI6eyJpZCI6MjEsInVzZXJuYW1lIjoiY291cG9uIiwiZW1haWwiOiJ0ZXN0QHRlc3QuY29tIiwicGFzc3dvcmQiOiJhMzg0YjY0NjNmYzIxNmE1ZjhlY2I2NjcwZjg2NDU2YSIsInJvbGUiOiJjdXN0b21lciIsImRlbHV4ZVRva2VuIjoiIiwibGFzdExvZ2luSXAiOiIxMjcuMC4wLjEiLCJwcm9maWxlSW1hZ2UiOiIvYXNzZXRzL3B1YmxpYy9pbWFnZXMvdXBsb2Fkcy9kZWZhdWx0LnN2ZyIsInRvdHBTZWNyZXQiOiIiLCJpc0FjdGl2ZSI6dHJ1ZSwiY3JlYXRlZEF0IjoiMjAyMi0xMi0yMFQwOTowNDowMi4yNzFaIiwidXBkYXRlZEF0IjoiMjAyMi0xMi0yMVQwNDoyNToyOC44NTRaIiwiZGVsZXRlZEF0IjpudWxsfSwiaWF0IjoxNjcxNTk2NzI5LCJleHAiOjE2NzE2MTQ3Mjl9.yHJMpCQUwDReEKC3MzxYkhPMCekagKa4D7hu1cJeikBN0sUgdiDP3F8x9LIk31nR3ouWyXDJiICkAeWoPXhbaTM3uZBzo3ILOS-dGYkvVzf8B391oD5mHWvmEWndvomY3xkRbAkukaZSCeJRnKHvp3xiz7yoiqUQzTcHrpVdVT0
Content-Type: application/json
Content-Length: 2
Origin: http://localhost:3000
DNT: 1
Connection: close
Cookie: language=en; welcomebanner_status=dismiss; cookieconsent_status=dismiss; continueCode=K9RqoL4yaBb3kJV0eXsDTxfkiJSDPHQbSqlCx9hnetaoGPp1xervYNWOgZzw; token=eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJzdGF0dXMiOiJzdWNjZXNzIiwiZGF0YSI6eyJpZCI6MjEsInVzZXJuYW1lIjoiY291cG9uIiwiZW1haWwiOiJ0ZXN0QHRlc3QuY29tIiwicGFzc3dvcmQiOiJhMzg0YjY0NjNmYzIxNmE1ZjhlY2I2NjcwZjg2NDU2YSIsInJvbGUiOiJjdXN0b21lciIsImRlbHV4ZVRva2VuIjoiIiwibGFzdExvZ2luSXAiOiIxMjcuMC4wLjEiLCJwcm9maWxlSW1hZ2UiOiIvYXNzZXRzL3B1YmxpYy9pbWFnZXMvdXBsb2Fkcy9kZWZhdWx0LnN2ZyIsInRvdHBTZWNyZXQiOiIiLCJpc0FjdGl2ZSI6dHJ1ZSwiY3JlYXRlZEF0IjoiMjAyMi0xMi0yMFQwOTowNDowMi4yNzFaIiwidXBkYXRlZEF0IjoiMjAyMi0xMi0yMVQwNDoyNToyOC44NTRaIiwiZGVsZXRlZEF0IjpudWxsfSwiaWF0IjoxNjcxNTk2NzI5LCJleHAiOjE2NzE2MTQ3Mjl9.yHJMpCQUwDReEKC3MzxYkhPMCekagKa4D7hu1cJeikBN0sUgdiDP3F8x9LIk31nR3ouWyXDJiICkAeWoPXhbaTM3uZBzo3ILOS-dGYkvVzf8B391oD5mHWvmEWndvomY3xkRbAkukaZSCeJRnKHvp3xiz7yoiqUQzTcHrpVdVT0
Sec-Fetch-Dest: empty
Sec-Fetch-Mode: cors
Sec-Fetch-Site: same-origin

{}
```

## Parameters 

### `<id>`

#### Description
Coupon code. Valid codes are 
```
l}6D#ga+jm (from chatbot)
l}6D#ga+sp (from twitter)
```

## Possible Attack Vectors

### ?


