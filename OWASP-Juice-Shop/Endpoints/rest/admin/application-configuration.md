## Connection Details

HTTP Methods: `GET`
Parameters: 
- `Authorization: Bearer <JWT Token>`

## Parameters 

### `Authorization: Bearer <JWT Token>`

#### Description
Login token used for access control. 

#### Sample
Encoded
```
eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJzdGF0dXMiOiJzdWNjZXNzIiwiZGF0YSI6eyJpZCI6MjEsInVzZXJuYW1lIjoidGVzdCIsImVtYWlsIjoidGVzdEB0ZXN0LmNvbSIsInBhc3N3b3JkIjoiYTM4NGI2NDYzZmMyMTZhNWY4ZWNiNjY3MGY4NjQ1NmEiLCJyb2xlIjoiY3VzdG9tZXIiLCJkZWx1eGVUb2tlbiI6IiIsImxhc3RMb2dpbklwIjoiMC4wLjAuMCIsInByb2ZpbGVJbWFnZSI6Ii9hc3NldHMvcHVibGljL2ltYWdlcy91cGxvYWRzL2RlZmF1bHQuc3ZnIiwidG90cFNlY3JldCI6IiIsImlzQWN0aXZlIjp0cnVlLCJjcmVhdGVkQXQiOiIyMDIyLTEyLTIwVDAzOjQxOjIxLjc0MloiLCJ1cGRhdGVkQXQiOiIyMDIyLTEyLTIwVDAzOjQyOjMwLjkwMVoiLCJkZWxldGVkQXQiOm51bGx9LCJpYXQiOjE2NzE1MDc3NTEsImV4cCI6MTY3MTUyNTc1MX0.vX2eZMOKwj58fXKr7yE-0LZA-39NG9CrfBAD1qj6HLLTel_OXzT1YaKFZOUSZE6ZExVtEvi2nLcJvJRsw7I67-h_GFTe16e95GY6o7V_huDEVewMxrA1AtbhSMm047vPo7af4i32aeUlsAtczuE55B0T7yhnmdnXXyJiOb4yrQE
```

Decoded:
```json
Header {
  "typ": "JWT",
  "alg": "RS256"
}

Payload {
  "status": "success",
  "data": {
    "id": 21,
    "username": "test",
    "email": "test@test.com",
    "password": "a384b6463fc216a5f8ecb6670f86456a",
    "role": "customer",
    "deluxeToken": "",
    "lastLoginIp": "0.0.0.0",
    "profileImage": "/assets/public/images/uploads/default.svg",
    "totpSecret": "",
    "isActive": true,
    "createdAt": "2022-12-20T03:41:21.742Z",
    "updatedAt": "2022-12-20T03:42:30.901Z",
    "deletedAt": null
  },
  "iat": 1671507751,
  "exp": 1671525751
}
```

## Possible Attack Vectors

### JWT Token
- [ ] Weak password
- [ ] None algorithm

