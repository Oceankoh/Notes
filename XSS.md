# Types of XSS

## Reflected XSS

Data is included from the user input and reflected in the web application without being made safe to render. In some cases, the user provided data may never leave the browser. 

## DOM-based XSS

Form of XSS where the entire tainted data flow from source to sink takes place in the browser. An example of this would be when the payload is supplied via the URL, e.g. `document.location.href`, and the sink is a sensitive method call that causes the execution of the malicious data, e.g. `document.write`. The key indicator the DOM is updated on the client-side via unsafe javascript. 

## Stored XSS

This is a form of persistent XSS. Data is stored in some form. When the user requests the page, the stored data is rendered on the browser resulting in an XSS. 

## Mutation XSS

## Universal XSS

# XSS Tricks 

## Slashes to split attributes

With a sink in a HTML element such as 

```js
<a ... href="<sink>"/>
```

Assuming you can escape the attribute with `"`, you could trigger XSS with various payloads such as `autofocus onfocus=alert(1)`. However, you could use slashses to split the attributes resulting in `autofocus/onfocus=alert(1)`. This would help to bypass any whitespace filters. 

## Using unicode parsing to decode into filtered characters

// TODO 

## Type Juggling to trigger function calls

Assuming you have a sink within a script tag, such as 

```js 
<script>
	var searchTerms = '<sink here>';
    document.write('<img src="/resources/images/tracker.gif?searchTerms='+encodeURIComponent(searchTerms)+'">');
</script>
```

If there are no filters, you could escape with `'; alert(1); //`
However, if `;` were filtered, it is still possible to execute functions via type juggling. A payload such as `' - alert(1) - '`, would cause js to perform arithmetic operations on the result of the function `alert(1)`, thus triggering the XSS. 

## Chaining `iframe` and `onresize` 

If you are able to embed the vulnerable website in an iframe, you might be able to cause an xss through the `onresize` event handler. To trigger this event, embed the website in an iframe deployed on attacker.com and resize it onload. Example as shown:

```js
<iframe src="vulnerablesite.com" onload=this.style.width='100px'>
```


# XSS Tips

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

Backticks in JS represent template strings. If there is an input is reflected in a template string, you can execute javascript with `${<js here}`.
