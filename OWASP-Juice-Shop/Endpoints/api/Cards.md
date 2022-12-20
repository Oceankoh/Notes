## Description

Returns JSON containing contents of user's cards. Authorization token required to view user's cards.

## Connection Details

HTTP Methods: `GET, POST`
Parameters: 
- `fullName`
- `cardNum`
- `expMonth`
- `expYear`

## POST Parameters 

### `fullName`
#### Description
Not required. Defaults to null. 

### `cardNum`
#### Description
Not required. Defaults to null. Validation performed to ensure `isInt` and `input >= 1000000000000000`. 

### `expMonth`
#### Description
Not required. Defaults to null. Validation checks to ensure `isInt` and `0 < input < 13`

### `expYear`
#### Description
Not required. Defaults to null. Validation checks to ensure `isInt` and  `2079 < input < 2100`

## Possible Attack Vectors

### ?


