## Description

Returns JSON containing contents of a user basket 

## Connection Details

HTTP Methods: `GET`
Parameters: 
- `UserId`
- `AddressId`
- `quantity`

### Sample Request
```http
POST /api/Recycles/ HTTP/1.1
Host: localhost:3000
User-Agent: Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:108.0) Gecko/20100101 Firefox/108.0
Accept: application/json, text/plain, */*
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Referer: http://localhost:3000/
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJzdGF0dXMiOiJzdWNjZXNzIiwiZGF0YSI6eyJpZCI6MSwidXNlcm5hbWUiOiIiLCJlbWFpbCI6ImFkbWluQGp1aWNlLXNoLm9wIiwicGFzc3dvcmQiOiIwMTkyMDIzYTdiYmQ3MzI1MDUxNmYwNjlkZjE4YjUwMCIsInJvbGUiOiJhZG1pbiIsImRlbHV4ZVRva2VuIjoiIiwibGFzdExvZ2luSXAiOiIiLCJwcm9maWxlSW1hZ2UiOiJhc3NldHMvcHVibGljL2ltYWdlcy91cGxvYWRzL2RlZmF1bHRBZG1pbi5wbmciLCJ0b3RwU2VjcmV0IjoiIiwiaXNBY3RpdmUiOnRydWUsImNyZWF0ZWRBdCI6IjIwMjItMTItMjAgMDQ6NTM6MzAuNzc0ICswMDowMCIsInVwZGF0ZWRBdCI6IjIwMjItMTItMjAgMDQ6NTM6MzAuNzc0ICswMDowMCIsImRlbGV0ZWRBdCI6bnVsbH0sImlhdCI6MTY3MTUyODMwNywiZXhwIjoxNjcxNTQ2MzA3fQ.hluVQNNTsAIuV0rl0KFQx0fUahkLDuwvuoHchwmujC37eTxr44TrO9vZjRlyEi3i039GVUv_T5tHwUOXEK2_tjRHmR6e6fXPNA811-6N0mj_JcG7tDMqkqZ8msNu2OsQUWVLNP3iduiZCC2rVQEy6VTWb5DUCLXAYjafI-lsf5M
Content-Type: application/json
Content-Length: 40
Origin: http://localhost:3000
DNT: 1
Connection: close
Cookie: language=en; welcomebanner_status=dismiss; cookieconsent_status=dismiss; continueCode=WovBXRLelZ6qD2xVyrEK9GQgsMTPfgimlHpjCJ4Ag5mkOMQj1Pnzp8Y47b3w; token=eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJzdGF0dXMiOiJzdWNjZXNzIiwiZGF0YSI6eyJpZCI6MSwidXNlcm5hbWUiOiIiLCJlbWFpbCI6ImFkbWluQGp1aWNlLXNoLm9wIiwicGFzc3dvcmQiOiIwMTkyMDIzYTdiYmQ3MzI1MDUxNmYwNjlkZjE4YjUwMCIsInJvbGUiOiJhZG1pbiIsImRlbHV4ZVRva2VuIjoiIiwibGFzdExvZ2luSXAiOiIiLCJwcm9maWxlSW1hZ2UiOiJhc3NldHMvcHVibGljL2ltYWdlcy91cGxvYWRzL2RlZmF1bHRBZG1pbi5wbmciLCJ0b3RwU2VjcmV0IjoiIiwiaXNBY3RpdmUiOnRydWUsImNyZWF0ZWRBdCI6IjIwMjItMTItMjAgMDQ6NTM6MzAuNzc0ICswMDowMCIsInVwZGF0ZWRBdCI6IjIwMjItMTItMjAgMDQ6NTM6MzAuNzc0ICswMDowMCIsImRlbGV0ZWRBdCI6bnVsbH0sImlhdCI6MTY3MTUyODMwNywiZXhwIjoxNjcxNTQ2MzA3fQ.hluVQNNTsAIuV0rl0KFQx0fUahkLDuwvuoHchwmujC37eTxr44TrO9vZjRlyEi3i039GVUv_T5tHwUOXEK2_tjRHmR6e6fXPNA811-6N0mj_JcG7tDMqkqZ8msNu2OsQUWVLNP3iduiZCC2rVQEy6VTWb5DUCLXAYjafI-lsf5M
Sec-Fetch-Dest: empty
Sec-Fetch-Mode: cors
Sec-Fetch-Site: same-origin

{"UserId":1,"AddressId":3,"quantity":10}
```

## Parameters 

### `?`

#### Description

#### Sample


## Possible Attack Vectors

### ?


