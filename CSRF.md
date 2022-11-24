# Testing for CSRF Vulnerabilities

## CSRF Token not tied to User Session

### Token tied to nothing

### Token tied to non-session cookie

## CRSF Token not required

## CSRF Token 

## Referrer

# 2 Hour Refresh Window

# Credentialed Requests

When using `fetch()` or `XMLHttpRequests`, by default no credentials are send for cross-origin requests. This means that the (session) cookies of a user will not be send even if the user has previously logged in to the site where the request is sent. 

However, if the sever does not repond with the header `Access-Control-Allow-Credentials: true`, the response would be ignored and not made available to the web content. This measure reduces the impact of CSRF attacks since they response is not received by the code. 