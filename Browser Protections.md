# CORS

CORS is an acronym for Cross-Origin Resource Sharing. It is a set of restrictions on third-party access to the content provided by a server. It is configured on the server via a set of response headers. 

## Response Headers
### Access-Control-Allow-Origin
Indicates whether the response can be shared with requesting code from the given origin. When nothing is set, the browser will not allow Cross Origin Requests, meaning that fetching from another api will result in an error. 

### Access-Control-Expose-Headers
Indicates which response headers are exposed to scripts running in the browser. This only applies to non-[CORS-safelisted response headers](https://developer.mozilla.org/en-US/docs/Glossary/CORS-safelisted_response_header)

### Access-Control-Max-Age
Indicates how long the results of a preflight request (information contained in Access-Control-Allow-Methods and Access-Control-Allow Headers) can be cached.

### Access-Control-Allow-Credentials
Tells the browser whether to expose rthe response to the frontend JavaScript code when the request's credentials mode is `include`. Credentials refer to cookies, authorization headers, or TLS Client certificates.

### Access-Control-Allow-Methods
Specifies one or more methods allowed when accessing a resource in response to a preflight request. 

### Access-Control-Allow-Headers
Specifies one or more headers allowed when accessing a resource in response to a preflight request. 

## Simple Requests

A simple request does not trigger a CORS preflight. A simple request is one that meets all the following conditions:

1. Method: `GET`, `HEAD`, `POST`
2. Only the following headers can be manually set:
	1. `Accept`
	2. `Accept-Language`
	3. `Content-Language`
	4. `Content-Type`: `application/x-www-form-urlencoded`, `multipart/form-data`, `text/plain`
	5. `Range`
3. No `ReadableStream` object is used in the request
4. No event listeners registered on the objected returned by `XMLHTTPRequest.upload`

## Preflight Requests

Unlike simply requests, the browser first sends a HTTP request using the `OPTIONS` method to the resource on the other origin, in order to determine if the actual request is safe to send. Such cross origin ruqets are preflighted since they may have implications for user data. 

![](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS/preflight_correct.png)

## Credentialed Requests

When using `fetch()` or `XMLHttpRequests`, by default no credentials are send for cross-origin requests. This means that the (session) cookies of a user will not be send even if the user has previously logged in to the site where the request is sent. 

Even if the request was intentionally formulated to send credentials, if the sever does not repond with the header `Access-Control-Allow-Credentials: true`, the response would be ignored and not made available to the web content. Additionally, when responding to credentialed requests, `Access-Control-Allow-Origin` should specify an explicit origin and not a wildcard. 

# CSP
CSP is short for Content Security Policy. It restricts the loading of content from untrusted sites. If configured correctly, this protects against XSS attacks by restricting where scripts can be loaded from. CSP can also enforce which protocols are used to transmit data. For example, a site can enforce that all content must be loaded with HTTPS as opposed to mixed content. This is usually the case since HTTPS ensures that both the server and the client know that they are receiving trusted, unmodified data. 

This can either be set in the HTTP response header, or in the `<HEAD></HEAD>` via `<meta>` tags in the HTML. 

# Cookie Protection

## Secure
A cookies with this attribute is only sent to the server via HTTPS. It is never sent via unsecured HTTP. 

## Same-Site
Lets servers specify whether/when cookies are sent with cross-site requests. There are 3 possible values for this, `Strict`, `Lax`, and `None`. With `Strict`, the browser only sends the cookie with requests from teh cookie's origin site. `Lax` is similar, except the browser also sends the cookie when the user nagvigates to the cookie's origin site (even if the user is coming from a different site). This enables automated sign-in when following links from different origin. `None` specifies that cookies re sent on both originating and cross-site requets, but only when the `Secure` attribute is set. Unless otherwise specified by the server, the default value assumed by the browser is `Lax`. 

## HttpOnly
Outlines whether the cookie is accessible to javascript. A cookie with this attribute is inaccessible to `Document.cookie`; it is only sent to the server. This would help to mitigate XSS attacks. 

## Domain & Path
Attributes that define the scope of the cookie: what URLs the cookies should be sent to. 

The `Domain` attribute specifies which hosts can receive a cookie. If unspecified, the attribute defaults to the same host that set the cookie, excluding subdomains. If Domain is specified, then subdomains are included. 

The `Path` attribute indicates a URL path that must exist in the requested URL in order to send the Cookie header. For example, if you set `Path=/docs`, these request paths match:
-   `/docs`
-   `/docs/`
-   `/docs/Web/`

But these request paths don't:
-   `/`
-   `/docsets`
-   `/fr/docs`

# X-Frame-Options
HTTP Response header that can be used to indicate whether or not a browser should be allowed to render a page in a `<frame>`, `<iframe>`, `<embed>` or `<object>`. Sites can use this to avoid click-jacking attacks, by ensuring that their content is not embedded into other sites.

There are two possible directives for `X-Frame-Options`: `DENY`, `SAMEORIGIN`. Omitting this header will allow other third-party sites to embed your site. 

# Header Spoofing

## Referer Policy

Prevent spoofing of referer header.



