# Authenticating with the APIs

The entrypoint to use for all requests is ​**[https://api.fliplet.com​](https://api.fliplet.com​)**. Alternatively, US clients can use ​**[https://us.api.fliplet.com​](https://us.api.fliplet.com​)** to get faster execution and response when their data resides in the US region (same applied for Canadian customers wanting to use ​**[https://ca.api.fliplet.com​](https://ca.api.fliplet.com​)**). If you’re unsure about this, please get in touch with us.

All requests must be made via ​**SSL​** to the above HTTPS-only endpoint.

All our APIs uses **​RESTful​ web services** which supports both **JSON** and url-encoded parameters as body of POST requests.

The request **body size ​limit​** on all endpoints is set to **1​ GB​**, which is then a hard limit for uploaded files.

**All requests must contain the authentication token** in the request headers ​or​ as a GET parameter. Alternatively, it can also be sent as a cookie, although sending it in the headers is preferred for security.

**Option 1) as a header**

```
Auth-token: eu--abcdefg123456789
```

Alternatively, you can also send the token via the **Authorization** header, encoded as a **base64**:

```
Authorization: Bearer ZXUtLWFiY2RlZmcxMjM0NTY3ODk=
```

**Option 2) as a GET parameter**
```
?auth_token=eu--abcdefg123456789
```

**Option 3) as a request cookie**
```
Cookie: auth_token=eu--abcdefg123456789;
```

If the provided token has been revoked, an error message will be returned as follows:

```json
{
  "error": "not authorised",
  "message":"The auth_token provided doesn't belong to any user."
}
```

## How to create an authentication token

1. Login to Fliplet Studio with your account
2. Edit the app you want to have API access to
3. Go to ‘App Settings’
4. Go to ‘App tokens’ tab of app settings
5. Create a new token

Note: The token does not expire, but can be revoked at any time should you want to (e.g. when unauthorized access is found or your token has been compromised).

<p class="quote">Some API endpoints may require you to use the app's production ID for extra added security, since app tokens don't have access to the working draft apps you see in Studio. You can grab the production app's ID by heading to the <strong>https://api.fliplet.com/v1/apps/</strong> endpoint and verify the value for the <code>productionAppId</code> for the apps you have access to</p>

---

All done? Jump to the [Data Sources](fliplet-datasources.md) documentation to start using our REST APIs!

[Next »](fliplet-datasources.md)
{: .buttons}
