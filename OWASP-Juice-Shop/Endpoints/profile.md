## Description

Returns JSON containing contents of a user basket 

## Connection Details

HTTP Methods: `GET, POST`
POST Parameters: 
- `username`

### Sample Request
```http
POST /profile HTTP/1.1
Host: localhost:3000
User-Agent: Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:108.0) Gecko/20100101 Firefox/108.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Referer: http://localhost:3000/profile
Content-Type: application/x-www-form-urlencoded
Content-Length: 14
Origin: http://localhost:3000
DNT: 1
Connection: close
Cookie: language=en; welcomebanner_status=dismiss; cookieconsent_status=dismiss; continueCode=WovBXRLelZ6qD2xVyrEK9GQgsMTPfgimlHpjCJ4Ag5mkOMQj1Pnzp8Y47b3w; token=eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJzdGF0dXMiOiJzdWNjZXNzIiwiZGF0YSI6eyJpZCI6MSwidXNlcm5hbWUiOiJhZG1pbiIsImVtYWlsIjoiYWRtaW5AanVpY2Utc2gub3AiLCJwYXNzd29yZCI6IjAxOTIwMjNhN2JiZDczMjUwNTE2ZjA2OWRmMThiNTAwIiwicm9sZSI6ImFkbWluIiwiZGVsdXhlVG9rZW4iOiIiLCJsYXN0TG9naW5JcCI6IiIsInByb2ZpbGVJbWFnZSI6ImFzc2V0cy9wdWJsaWMvaW1hZ2VzL3VwbG9hZHMvZGVmYXVsdEFkbWluLnBuZyIsInRvdHBTZWNyZXQiOiIiLCJpc0FjdGl2ZSI6dHJ1ZSwiY3JlYXRlZEF0IjoiMjAyMi0xMi0yMFQwNDo1MzozMC43NzRaIiwidXBkYXRlZEF0IjoiMjAyMi0xMi0yMFQwOTo1Njo0MC42NzhaIiwiZGVsZXRlZEF0IjpudWxsfSwiaWF0IjoxNjcxNTMwMjAxLCJleHAiOjE2NzE1NDgyMDF9.rTsY0ldQPEBmgJIzH69bPrEl6PIcCRNJuDRp1gtridr308G6A6o8hQaEYE0SjsjsePI-chQuHxDxU0hanphIf80D64AcwExkg6Sspdkg9_utLWtBHNyWplnPsjAuBuyFCwgUX0HaBQiUOafh-qpQodO-BQRMpHqTkAmyqM3Muyw
Upgrade-Insecure-Requests: 1
Sec-Fetch-Dest: document
Sec-Fetch-Mode: navigate
Sec-Fetch-Site: same-origin
Sec-Fetch-User: ?1

username=admin
```

## Parameters 

### `?`

#### Description

#### Sample


## Possible Attack Vectors

### HTML Injection username

#### Exploit 
1. Use POST request to set username
2. Load page

#### Impact

No impact? Only user profile is affected thus far. 
Can other users view the profile? 
Is the username reflected anywhere else? 
