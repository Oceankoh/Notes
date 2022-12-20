## Description

Nothing much in the HTML other than a bunch of references to scripts. Response for server scripts contain additional headers. 

##### From Server
- `runtime.js`
- `polyfills.js`
- `main.js`
- `vendor.js`

##### From Cloud 
- `jquery 2.2.4`
- `cookieconsent2 3.1.0`

## Connection Details

HTTP Methods: `GET`
Parameters: 
- `?`

## Parameters 
### `?`

#### Description

#### Sample

## Vulnerabilities

### Reflected XSS in `q` parameter

#### Description
Reflected XSS in search results. 

#### Payload 
`http://localhost:3000/#/search?q=<img src=x onerror=alert(1)>`

## Possible Attack Vectors

### ?