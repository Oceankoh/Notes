## Description

GET request returns list of all users on the platform. POST request is used to register for a new user account. 

## Connection Details

HTTP Methods: `POST`, `GET`
Parameters: 
- `email`
- `password`
- `passwordRepeat`
- `role`

### Sample Request

```http
POST /api/Users/ HTTP/1.1
Host: 127.0.0.1:3000
User-Agent: Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:108.0) Gecko/20100101 Firefox/108.0
Accept: application/json, text/plain, */*
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Referer: http://127.0.0.1:3000/
Content-Type: application/json
Content-Length: 106
Origin: http://127.0.0.1:3000
DNT: 1
Connection: close
Sec-Fetch-Dest: empty
Sec-Fetch-Mode: cors
Sec-Fetch-Site: same-origin

{"email":"asdfaaa","password":"asdf","passwordRepeat":"asdf",
"role":"admin"}
```

## Parameters 

### `email`
#### Description
Checks are performed to ensure field is unique. However no check is done to ensure email format is valid. 

### `role`
#### Description
Determines account role. 

## Vulnerabilities
### Lack of authentication 

#### Exploit
Specify `"role":"admin"` when registering for account. 

#### Impact
Unpriviledged user can regsiter for admin account. 

## Possible Attack Vectors

### ?


