# Microservice API  - Documentation
### Gateway
This documents all the information required to interact with the gateway as a _**client**_, remember to take this into account when writing URLs.
###  Token <a id='token'></a>
The API uses two types of tokens. Authentication and refresh tokens in the form of JWT. Each JWT token has a lifetime.

Type  | Lifetime
------------- | -------------
Refresh Token | 30 minutes
Authorisation Token  | 10 minutes 

#### Expired Tokens
Using any expired token will cause all generations of that token to be invalidates as well.

## Get Authorisation Token
To consume services provided by the API, you must be authorised. Any unauthorised requests will **not** be passed to services.

```sh
POST api/login
```
>Parameters: `{Required}`, `[Optional]`, `<variables\>`

The body will contain **username** **password** in the form of json.
```sh
{
	"username": "<User>", 
	"password": "<Pass>"
}
```
The gateway will return 2 things, an authorisation token, and a refresh token.
```sh
{
	"refreshToken": "<R-Token>",
	"authToken": "<A-Token>"
 }
```
When making a request to a service, _**A-**_**Token** must be present in the **Authorisation** header.

## Refreshing the Authorisation Token
Authorisation tokens need to be refreshed because they expire (See [Tokens](#token))
```sh
POST api/refresh
```
>Parameters: `{Required}`, `[Optional]`, `<variables\>`

When making a request to a gateway refresh endpoint,** R-Token** must be present in the **Refresh** header.
The gateway will return 2 things, an authorisation token, and a refresh token.

```sh
{
	"refreshToken": "<R-Token>",
	"authToken": "<A-Token>"
}
```


> Documentation
By  Developer Callum👨‍💻

## to be continue...
