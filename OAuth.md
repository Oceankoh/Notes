OAuth 2.0 is a framework that enables applications to request limited access to user data from a resource server. 

The general procsess is as follows: 

1. Client Application request access to some subset of user data, specifying hwich grant type and access they require
2. User is prompted to log in to the OAuth system and give consent for requested access
3. Client application receives a unique access token that proves they have permission from the user to acccess the requested data
4. Client application uses this token to make API calls to the resorruce server

# Grant Types

Often refered to as OAuth flows since grant types determines the exact sequence of steps that are involvedin the OAuth process. 

## Implicit Grant Type

ideal for lean applications such as SPAs which cannot easily store the `client_secret` on the backend. This `client_secret` is stored on the client instead (such as in browser local storage). After the user provides consent, the OAuth service redirects the user's browser to the callback URL with the `access_token` and other information in the URL fragment. The information contained within the fragment is stored on the client. 

## Authorization Code Grant Type

After the user provides consent, the OAuth service redirects the user's browser to the callback URL with the authorization code contained as a query parameter. In other words, the user is forwarding the authorization code from the OAuth service to the application backend. The application server can use this authorization code to request for an access token from the OAuth service. During this exchange, the OAuth service will validate the authorization code and respond with the access token along with its available scope.  