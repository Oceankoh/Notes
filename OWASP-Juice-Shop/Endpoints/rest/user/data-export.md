## Description

Returns JSON containing contents of a user basket 

## Connection Details

HTTP Methods: `GET`
Parameters: 
- `?`

### Sample Request

```http

```

## Parameters 

### `?`

#### Description

#### Sample

## Vulnerabilities

### Captcha Bypass

#### Description
Application relies on client to request captcha reset. If captcha is not reset, previous captcha answer remains valid. 
Additionally, captcha answer is sent along wth the challenge. 

#### Impact
Captcha is ineffective in preventing spam. 

## Possible Attack Vectors

### ?


