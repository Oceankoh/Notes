## Description

View/Add complaint. 

## Connection Details

HTTP Methods: `GET, POST`
POST Parameters: 
- `file`
- `UserId`
- `message`

### Sample Request

```http
POST /api/Complaints/ HTTP/1.1
Host: localhost:3000
User-Agent: Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:108.0) Gecko/20100101 Firefox/108.0
Accept: application/json, text/plain, */*
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Referer: http://localhost:3000/
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJzdGF0dXMiOiJzdWNjZXNzIiwiZGF0YSI6eyJpZCI6MjEsInVzZXJuYW1lIjoiY291cG9uIiwiZW1haWwiOiJ0ZXN0QHRlc3QuY29tIiwicGFzc3dvcmQiOiJhMzg0YjY0NjNmYzIxNmE1ZjhlY2I2NjcwZjg2NDU2YSIsInJvbGUiOiJkZWx1eGUiLCJkZWx1eGVUb2tlbiI6ImUyNDNiMGYyMjE5M2MzY2U5NTUxNTVjN2Q3ZTNlYWYyY2I3Yzc2YzdkNTI2MmM2OTQ0ZTNmODc5MWVjMzI0MDciLCJsYXN0TG9naW5JcCI6IjEyNy4wLjAuMSIsInByb2ZpbGVJbWFnZSI6Ii9hc3NldHMvcHVibGljL2ltYWdlcy91cGxvYWRzL2RlZmF1bHQuc3ZnIiwidG90cFNlY3JldCI6IiIsImlzQWN0aXZlIjp0cnVlLCJjcmVhdGVkQXQiOiIyMDIyLTEyLTIwVDA5OjA0OjAyLjI3MVoiLCJ1cGRhdGVkQXQiOiIyMDIyLTEyLTIxVDA2OjM2OjQxLjA5OVoiLCJkZWxldGVkQXQiOm51bGx9LCJpYXQiOjE2NzE2MDQ2MDEsImV4cCI6MTY3MTYyMjYwMX0.THof4W67Gh0oAFI9yGaNDTEokkkGRw6mKZsCVXmhsSKaRY97kuTL3pW7Jsc8lmkM8CrhXXcYTNLxQ1B_tTKs2AS4lt0MP2ATh-98wppLS2BJA1R5_W5L2N7yJKZVlELEms80mp6Ct38iYRofQYFae7JMnBy9M7mOcS8eyI5DknY
Content-Type: application/json
Content-Length: 55
Origin: http://localhost:3000
DNT: 1
Connection: close
Cookie: language=en; welcomebanner_status=dismiss; cookieconsent_status=dismiss; continueCode=gDoB5294JnRaeLA4XsjUMT1f1iySBvHzMSWDCrPhRNtpkArPKQy37Ywb6Vxl; token=eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJzdGF0dXMiOiJzdWNjZXNzIiwiZGF0YSI6eyJpZCI6MjEsInVzZXJuYW1lIjoiY291cG9uIiwiZW1haWwiOiJ0ZXN0QHRlc3QuY29tIiwicGFzc3dvcmQiOiJhMzg0YjY0NjNmYzIxNmE1ZjhlY2I2NjcwZjg2NDU2YSIsInJvbGUiOiJkZWx1eGUiLCJkZWx1eGVUb2tlbiI6ImUyNDNiMGYyMjE5M2MzY2U5NTUxNTVjN2Q3ZTNlYWYyY2I3Yzc2YzdkNTI2MmM2OTQ0ZTNmODc5MWVjMzI0MDciLCJsYXN0TG9naW5JcCI6IjEyNy4wLjAuMSIsInByb2ZpbGVJbWFnZSI6Ii9hc3NldHMvcHVibGljL2ltYWdlcy91cGxvYWRzL2RlZmF1bHQuc3ZnIiwidG90cFNlY3JldCI6IiIsImlzQWN0aXZlIjp0cnVlLCJjcmVhdGVkQXQiOiIyMDIyLTEyLTIwVDA5OjA0OjAyLjI3MVoiLCJ1cGRhdGVkQXQiOiIyMDIyLTEyLTIxVDA2OjM2OjQxLjA5OVoiLCJkZWxldGVkQXQiOm51bGx9LCJpYXQiOjE2NzE2MDQ2MDEsImV4cCI6MTY3MTYyMjYwMX0.THof4W67Gh0oAFI9yGaNDTEokkkGRw6mKZsCVXmhsSKaRY97kuTL3pW7Jsc8lmkM8CrhXXcYTNLxQ1B_tTKs2AS4lt0MP2ATh-98wppLS2BJA1R5_W5L2N7yJKZVlELEms80mp6Ct38iYRofQYFae7JMnBy9M7mOcS8eyI5DknY
Sec-Fetch-Dest: empty
Sec-Fetch-Mode: cors
Sec-Fetch-Site: same-origin

{"UserId":21,"message":"asdf",
"file":"/etc/passwd"
}
```

## Parameters 

### `?`

#### Description

#### Sample

## Vulnerabilities

### Name

#### Exploit

#### Impact

## Possible Attack Vectors

### ?


