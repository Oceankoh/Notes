## Description

Presumably checks if the account username is set. If it isn't, it will ask for a value. However if current value of username is `"`, endpoint will return 

```json
{
  "error": {
    "message": "Blocked illegal activity by ::ffff:127.0.0.1",
    "stack": "Error: Blocked illegal activity by ::ffff:127.0.0.1\n    at /home/ocean/Desktop/juice-shop/build/routes/chatbot.js:175:22"
  }
}
```

## Connection Details

HTTP Methods: `GET`
Parameters: 
- `None`

### Sample Request

```http
GET /rest/chatbot/status HTTP/1.1
Host: localhost:3000
User-Agent: Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:108.0) Gecko/20100101 Firefox/108.0
Accept: application/json, text/plain, */*
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Referer: http://localhost:3000/
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJzdGF0dXMiOiJzdWNjZXNzIiwiZGF0YSI6eyJpZCI6MjEsInVzZXJuYW1lIjoiY291cG9uIiwiZW1haWwiOiJ0ZXN0QHRlc3QuY29tIiwicGFzc3dvcmQiOiJhMzg0YjY0NjNmYzIxNmE1ZjhlY2I2NjcwZjg2NDU2YSIsInJvbGUiOiJkZWx1eGUiLCJkZWx1eGVUb2tlbiI6ImUyNDNiMGYyMjE5M2MzY2U5NTUxNTVjN2Q3ZTNlYWYyY2I3Yzc2YzdkNTI2MmM2OTQ0ZTNmODc5MWVjMzI0MDciLCJsYXN0TG9naW5JcCI6IjEyNy4wLjAuMSIsInByb2ZpbGVJbWFnZSI6Ii9hc3NldHMvcHVibGljL2ltYWdlcy91cGxvYWRzL2RlZmF1bHQuc3ZnIiwidG90cFNlY3JldCI6IiIsImlzQWN0aXZlIjp0cnVlLCJjcmVhdGVkQXQiOiIyMDIyLTEyLTIwIDA5OjA0OjAyLjI3MSArMDA6MDAiLCJ1cGRhdGVkQXQiOiIyMDIyLTEyLTIxIDA2OjM2OjQxLjA5OSArMDA6MDAiLCJkZWxldGVkQXQiOm51bGx9LCJpYXQiOjE2NzE2MTAwNzUsImV4cCI6MTY3MTYyODA3NX0.ltc0v1BWn96kCGThrb-YyTRxNPuj2u8nm_aJPEHm8_2U1NRtswUb4JO8VHKVb2hrdEu8otDuBOsPo0PoKrm7lZz76VQ_uyaebPgEotdmNl6vYI3A4A-eDtSpRprkWKQr-l3JyUQ28fD0-Lqb-arRT27A6PX3EYhz9iaTAWVJSy0
DNT: 1
Connection: close
Cookie: language=en; welcomebanner_status=dismiss; cookieconsent_status=dismiss; continueCode=oLXzErxk5aQm1Gn4tKsyUPTpfbiDSROH1Vfo8CY6h9xI4mA2W8DgOM4pKJjq; token=eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJzdGF0dXMiOiJzdWNjZXNzIiwiZGF0YSI6eyJpZCI6MjEsInVzZXJuYW1lIjoiIiwiZW1haWwiOiJ0ZXN0QHRlc3QuY29tIiwicGFzc3dvcmQiOiJhMzg0YjY0NjNmYzIxNmE1ZjhlY2I2NjcwZjg2NDU2YSIsInJvbGUiOiJkZWx1eGUiLCJkZWx1eGVUb2tlbiI6ImUyNDNiMGYyMjE5M2MzY2U5NTUxNTVjN2Q3ZTNlYWYyY2I3Yzc2YzdkNTI2MmM2OTQ0ZTNmODc5MWVjMzI0MDciLCJsYXN0TG9naW5JcCI6IjEyNy4wLjAuMSIsInByb2ZpbGVJbWFnZSI6Ii9hc3NldHMvcHVibGljL2ltYWdlcy91cGxvYWRzL2RlZmF1bHQuc3ZnIiwidG90cFNlY3JldCI6IiIsImlzQWN0aXZlIjp0cnVlLCJjcmVhdGVkQXQiOiIyMDIyLTEyLTIwVDA5OjA0OjAyLjI3MVoiLCJ1cGRhdGVkQXQiOiIyMDIyLTEyLTIxVDA4OjA5OjE0LjQ1OVoiLCJkZWxldGVkQXQiOm51bGx9LCJpYXQiOjE2NzE2MTAxNTQsImV4cCI6MTY3MTYyODE1NH0.oQ5lYXsrLZlPaa_w_mCxO4KfcNvLwyXVJJMPsuxCLB5sLIwdq6J8q5Hm8kDtVQO-fSINCLQBFcIVlRfyUVkraT1e47sXnejoPsswHp8O_GG64fY_vnBt9CqiujqHuGNj2PoCrBOr_U5YYysW5zdR3W48WIZxfhIJKmx9eT5ROmI
Sec-Fetch-Dest: empty
Sec-Fetch-Mode: cors
Sec-Fetch-Site: same-origin
If-None-Match: W/"58-m8V3FIrSL224h1kPmtYx3djkb90"


```
## Vulnerabilities

### Username Injection

## Possible Attack Vectors

### -


