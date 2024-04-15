---
sidebar_position: 3
---

# Session Login

Session Login is ideal for in-app authentication. It allows users to authenticate within your app using Ziqx Auth. This method involves sending a POST request to generate a session token, redirecting the user to the Ziqx Auth session URL, and validating the session.

## Prerequisites

Before implementing Auth-Code Login with Ziqx Auth, make sure you have registered your app at the **[Ziqx Developers Console](https://developers.ziqx.cc)**. Upon registration, you will obtain the `app_key` and `app_secret` required for authentication.

## Implementation Steps

1. **Generate Session Token**:
   Send a `POST` request to the following endpoint:
   ```
   https://account.ziqx.cc/session/generate/
   ```
Include the `app_key` and `app_secret` in the request body.
```json
{
  "app_key": "your_app_key",
  "app_secret": "your_app_secret"
}
```

The response will contain a session token (token) and session ID (session_id).

2. **Redirect User:**:
Redirect the user to the session URL obtained from the response:
```
response['base_url'] + response['token']
```
For example: `https://account.ziqx.cc/console/session/{token}.`

3. **Validate Session:**
To validate the session, send a `POST` request to the following endpoint:
```
https://account.ziqx.cc/session/validate/
```
Include the session_id obtained from the previous step in the request body.

```json
{
  "session_id": "session_id",
}

```

Ensure that the request content type is set to `"application/x-www-form-urlencoded"` or send as `formdata`.

## Example
Here's an example implementation in Python using the requests library:

```python
import requests

# Step 1: Generate Session Token
body={
    "app_key": "your_app_key", 
    "app_secret": "your_app_secret"
     }
response = requests.post("https://account.ziqx.cc/session/generate/", json=body)

data = response.json()
session_id = data["session_id"]

# Step 2: Redirect User
redirect_url = data["base_url"] + data["token"]
# Implement redirect logic in your app

# Step 3: Validate Session
body = {"session_id": session_id}
validate_response = requests.post("https://account.ziqx.cc/session/validate/", json=body)

```
