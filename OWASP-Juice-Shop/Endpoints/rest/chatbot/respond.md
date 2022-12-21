## Description

Send message to chatbot.

## Connection Details

HTTP Methods: `POST`
Parameters: 
- `action`
- `query`

### Sample Request

```http
POST /rest/chatbot/respond HTTP/1.1
Host: localhost:3000
User-Agent: Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:108.0) Gecko/20100101 Firefox/108.0
Accept: application/json, text/plain, */*
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Referer: http://localhost:3000/
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJzdGF0dXMiOiJzdWNjZXNzIiwiZGF0YSI6eyJpZCI6OSwidXNlcm5hbWUiOiI8aW1nPiIsImVtYWlsIjoiSjEyOTM0QGp1aWNlLXNoLm9wIiwicGFzc3dvcmQiOiIzYzJhYmMwNGU0YTZlYThmMTMyN2QwYWFlMzcxNGI3ZCIsInJvbGUiOiJhZG1pbiIsImRlbHV4ZVRva2VuIjoiIiwibGFzdExvZ2luSXAiOiIiLCJwcm9maWxlSW1hZ2UiOiJhc3NldHMvcHVibGljL2ltYWdlcy91cGxvYWRzL2RlZmF1bHRBZG1pbi5wbmciLCJ0b3RwU2VjcmV0IjoiIiwiaXNBY3RpdmUiOnRydWUsImNyZWF0ZWRBdCI6IjIwMjItMTItMjBUMDQ6NTM6MzAuNzc1WiIsInVwZGF0ZWRBdCI6IjIwMjItMTItMjFUMDc6NDk6MTguMTg1WiIsImRlbGV0ZWRBdCI6bnVsbH0sImlhdCI6MTY3MTYwODk1OCwiZXhwIjoxNjcxNjI2OTU4fQ.M_NmhJZAid0p6kKHM08-RAUFqukUP20PcZ7zM6fp1IUZ-4qo97nqrSocH_XU2Ge8J5knSUnyNp_T7sILh0meQCopayPeXktPZWmTUzLCrixKkFpjnWPsDk59oUvVfcKOXKmV8VKGvcAHH1WQT1hSkVwjmtOxPH3pMAOLYdnELQA
Content-Type: application/json
Content-Length: 100
Origin: http://localhost:3000
DNT: 1
Connection: close
Cookie: language=en; welcomebanner_status=dismiss; cookieconsent_status=dismiss; continueCode=oLXzErxk5aQm1Gn4tKsyUPTpfbiDSROH1Vfo8CY6h9xI4mA2W8DgOM4pKJjq
Sec-Fetch-Dest: empty
Sec-Fetch-Mode: cors
Sec-Fetch-Site: same-origin

{"action":"query","query":"coupon"}
```

## Parameters 

### `action`
#### Description
Available values are `query`, `setname`. 
`setname` is used when account `username` has not already been set. However, trying to set username to `"` hangs the response. If username has already been set to `"` through `/profile`, `/rest/chatbot/respond` will return a response. 

### `query`
#### Description
Contains message read by the chatbot. Sending the value `coupon` cycles it through various messages, of which one of them gives you a 10% coupon. No other messages seem to illicit any interesting behavior. 

Application accepts sending an object, but it's contents does not seem to matter. Bot is able to read strings stored in an array just fine. `"query":[1,2,"coupon"]` returns identical responses as `"query":"coupon"`.

## Vulnerabilities

### Command Injection

#### Exploit

#### Impact

## Possible Attack Vectors

### Command Injection

#### Observed Behavior
Setting `" - "` as username in `/profile` causes the chatbot to evaluate it to `0`.  Using the value `" - true - "` evaluates to `-1`. `" + Object.toString() + "` results in `Nice to meet you function Object() { [native code] }, I'm Juicy`.

`console.log` and `alert` fails -> should be server side execution? 

