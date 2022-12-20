## Description

Returns JSON containing contents of a user basket 

## Connection Details

HTTP Methods: `GET,HEAD,PUT,PATCH,POST,DELETE`
Parameters: 
- `<id>`

## Parameters 

### `id`

#### Description

Presumably accepts an integer as ID, but there is no validation done on the input. No verification checks. 

#### Sample

## Vulnerabilities

### IDOR on `id` field

#### Exploit 
Change id to any number

#### Impact
Able to view other users basket. 

## Possible Attack Vectors

- [x] IDOR
- [ ] Injections


