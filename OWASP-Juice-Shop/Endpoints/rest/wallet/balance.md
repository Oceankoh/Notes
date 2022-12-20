## Description

Add money to wallet (PUT) and view balance of wallet (GET). Authorization header required to view balance.

## Connection Details

HTTP Methods: `PUT, GET`
Parameters: 
- `balance`
- `paymentId`

## PUT Parameters 

### `balance`
#### Description
No validation done to ensure balance is an integer

### `paymentId`
#### Description
Some checks are done. `paymentId < 7` fails. 

## Possible Attack Vectors

### ?


