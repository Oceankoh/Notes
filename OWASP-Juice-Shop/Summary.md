## Description

Juice Shop. Application seems to be a standard e-commerce site that sells juice. Users have to create accounts to buy juice. 

## Scope

### `/`

#### Description

Nothing much in the HTML other than a bunch of references to scripts. Response for server scripts contain additional headers. 

##### From Server
- `runtime.js`
- `polyfills.js`
- `main.js`
- `vendor.js`

##### From Cloud 
- `jquery 2.2.4`
- `cookieconsent2 3.1.0`

### `/rest/admin/application-configuration`

#### Description
Returns JSON containing content to populate the juice shop according to provided JWT.  

## Environment

### Libraries
#### Angular JS
##### Evidence
`GET /rest/basket/` returns 
```json
...
Error: Unexpected path: /rest/basket/\n    at /home/ocean/Desktop/juice-shop/build/routes/angular.js 
...
```

#### Express ^4.17.1
##### Evidence
[http://localhost:3000/ftp/suspicious_errors.yml](http://localhost:3000/ftp/suspicious_errors.yml) returns 
```
OWASP Juice Shop (Express ^4.17.1)
```

#### Express-jwt
##### Evidence
`GET /rest/basket/` returns 
```json
...
(/home/ocean/Desktop/juice-shop/node_modules/express-jwt/node_modules/jsonwebtoken/index.js:59:3)...
```
#### sequelize
##### Evidence
`POST /api/Feedbacks/` returns 
```json
...
"message": "WHERE parameter \"captchaId\" has invalid \"undefined\" value",
"stack": "Error: WHERE parameter \"captchaId\" has invalid \"undefined\" value\n    at SQLiteQueryGenerator.whereItemQuery (/home/ocean/Desktop/juice-shop/node_modules/sequelize/lib/dialects/abstract/query-generator.js:1693:13) 
...
```

#### busboy
##### Evidence
`POST /rest/memories` with malformed body returns
```
(/home/ocean/Desktop/juice-shop/node_modules/busboy/lib/types/multipart.js:398:32)
```

#### streamsearch
##### Evidence
`POST /rest/memories` with malformed body returns
```
(/home/ocean/Desktop/juice-shop/node_modules/streamsearch/lib/sbmh.js:104:16)
```
## Credentials 

### admin login credentials
Leaked from SQLi login returning authentication token containing MD5 of admin account password. Cracking the hash returns the password. 

```
admin@juice-sh.op:admin123
```

## Vulnerabilities

### SQLi in `/rest/user/login`
### IDOR at `/rest/basket/<id>`
### IDOR at `/ftp/`
### Reflected XSS in `q` param at `/#/search?q=`
### Stored XSS at `/#/administration` and `/#/about` from `/api/Feedbacks/`
### Broken authentication in account registration at `/api/Users`

	
