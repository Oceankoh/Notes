## Content Security Policy

Workers are considered to have their own execution context, distinct from the document that created them. For this reason they are, in general, not governed by the [content security policy](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions/Content_Security_Policy) of the document (or parent worker) that created them. So for example, suppose a document is served with the following header:

```
Content-Security-Policy: script-src 'self'
```

Among other things, this will prevent any scripts it includes from using [`eval()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/eval). However, if the script constructs a worker, code running in the worker's context _will_ be allowed to use `eval()`.