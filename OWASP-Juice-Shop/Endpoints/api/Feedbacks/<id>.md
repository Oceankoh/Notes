## Description

Delete feedback of specified id. Customer feedback seems to be limited to 100 entries. Endpoint useful to clear history. 

## Connection Details

HTTP Methods: `DELETE`
Parameters: 
- `<id>`

### Sample Request

```http
DELETE /api/Feedbacks/17 HTTP/1.1
Host: localhost:3000
User-Agent: Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:108.0) Gecko/20100101 Firefox/108.0
Accept: application/json, text/plain, */*
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Referer: http://localhost:3000/
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJzdGF0dXMiOiJzdWNjZXNzIiwiZGF0YSI6eyJpZCI6OSwidXNlcm5hbWUiOiIiLCJlbWFpbCI6IkoxMjkzNEBqdWljZS1zaC5vcCIsInBhc3N3b3JkIjoiM2MyYWJjMDRlNGE2ZWE4ZjEzMjdkMGFhZTM3MTRiN2QiLCJyb2xlIjoiYWRtaW4iLCJkZWx1eGVUb2tlbiI6IiIsImxhc3RMb2dpbklwIjoiIiwicHJvZmlsZUltYWdlIjoiYXNzZXRzL3B1YmxpYy9pbWFnZXMvdXBsb2Fkcy9kZWZhdWx0QWRtaW4ucG5nIiwidG90cFNlY3JldCI6IiIsImlzQWN0aXZlIjp0cnVlLCJjcmVhdGVkQXQiOiIyMDIyLTEyLTIwIDA0OjUzOjMwLjc3NSArMDA6MDAiLCJ1cGRhdGVkQXQiOiIyMDIyLTEyLTIwIDA0OjUzOjMwLjc3NSArMDA6MDAiLCJkZWxldGVkQXQiOm51bGx9LCJpYXQiOjE2NzE2MDUyMjcsImV4cCI6MTY3MTYyMzIyN30.GtWaxzfNnE9yCNDzOebIUT2ldMt1W5TV39FfxhD-cSuySu4O6Sbc0C4JYzHNZYGFHTfJHCs4yczoXTi4o6MJY48anNB0xajsHXlb9N9gMVdwb1xQcZmYAw-3rK6jtWanWvYLMyBF41klxPXBVSHtijLgpZdlkTtwQQ8-KCLGCQQ
Origin: http://localhost:3000
DNT: 1
Connection: close
Cookie: language=en; welcomebanner_status=dismiss; cookieconsent_status=dismiss; continueCode=oLXzErxk5aQm1Gn4tKsyUPTpfbiDSROH1Vfo8CY6h9xI4mA2W8DgOM4pKJjq; token=eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJzdGF0dXMiOiJzdWNjZXNzIiwiZGF0YSI6eyJpZCI6OSwidXNlcm5hbWUiOiIiLCJlbWFpbCI6IkoxMjkzNEBqdWljZS1zaC5vcCIsInBhc3N3b3JkIjoiM2MyYWJjMDRlNGE2ZWE4ZjEzMjdkMGFhZTM3MTRiN2QiLCJyb2xlIjoiYWRtaW4iLCJkZWx1eGVUb2tlbiI6IiIsImxhc3RMb2dpbklwIjoiIiwicHJvZmlsZUltYWdlIjoiYXNzZXRzL3B1YmxpYy9pbWFnZXMvdXBsb2Fkcy9kZWZhdWx0QWRtaW4ucG5nIiwidG90cFNlY3JldCI6IiIsImlzQWN0aXZlIjp0cnVlLCJjcmVhdGVkQXQiOiIyMDIyLTEyLTIwIDA0OjUzOjMwLjc3NSArMDA6MDAiLCJ1cGRhdGVkQXQiOiIyMDIyLTEyLTIwIDA0OjUzOjMwLjc3NSArMDA6MDAiLCJkZWxldGVkQXQiOm51bGx9LCJpYXQiOjE2NzE2MDUyMjcsImV4cCI6MTY3MTYyMzIyN30.GtWaxzfNnE9yCNDzOebIUT2ldMt1W5TV39FfxhD-cSuySu4O6Sbc0C4JYzHNZYGFHTfJHCs4yczoXTi4o6MJY48anNB0xajsHXlb9N9gMVdwb1xQcZmYAw-3rK6jtWanWvYLMyBF41klxPXBVSHtijLgpZdlkTtwQQ8-KCLGCQQ
Sec-Fetch-Dest: empty
Sec-Fetch-Mode: cors
Sec-Fetch-Site: same-origin


```

## Possible Attack Vectors

### ?

