# Authentication

To connect to our API you must use the `Authorization` header after successfully authenticating as a user.

### Signing in

To authenticate an existing user in exchange for a token, send a `POST` request to the `/v1/auth/token` endpoint.

This request must contain the email address and password of the account you'd like to access, along with the name of the device sending the request.

```curl
$ curl https://api.dodays.co.uk/v1/auth/token \
    -H "Accept: application/json" \
    -d email="demo@dodays.co.uk" \
    -d password="password" \
    -d device_name="Device"
```

If your request succeeds, a new token will be returned for you to access the users account.

```json
{
  "token": "API_TOKEN"
}
```

### Using an API token

Once a user has been authenticated and you have received an API token, this can be used in subsequent requests to access the users account.

Tokens expire after 72 hours, at which point the user will need re-authenticating in exchange for a new token.

In order to verify the user is still authenticated and the token hasn't expired, you can send a `GET` request to the `/v1/whoami` endpoint.

```curl
$ curl https://api.dodays.co.uk/v1/whoami \
    -H "Authorization: Bearer API_TOKEN"
```

If your request succeeds, the `User` object will be returned.

```json
{
  "data": {
    "id": 1,
    "first_name": "Demo",
    "last_name": "Customer",
    "email": "demo@dodays.co.uk",
    "telephone": "01913334444",
    "street": null,
    "town": null,
    "postcode": null,
    "emergency_name": null,
    "emergency_telephone": null,
    "emergency_relationship": null,
    "activated_at": "2020-01-01T12:00:00.000000Z"
  }
}
```
