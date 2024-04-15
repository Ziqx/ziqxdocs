---
sidebar_position: 2
---

# Redirect Login

Ziqx Auth provides a convenient way to implement redirect login for your app or website. With redirect login, users can seamlessly authenticate using Ziqx Auth and be redirected to your specified URL upon successful authentication.

## Prerequisites

Before implementing redirect login with Ziqx Auth, make sure you have registered your app at the [Ziqx Developers Console](https://developers.ziqx.cc). Upon registration, you will receive an `appKey` that you'll use to initiate the redirect login flow.

## Implementation

To implement redirect login with Ziqx Auth, follow these steps:

1. **Register Your App**: Register your app at the Ziqx Developers Console and obtain your `appKey`.

2. **Redirect the User**: Redirect the user to the Ziqx Auth login page using the following URL format:
```https://account.ziqx.cc?appId={appKey}```

Replace `{appKey}` with the `appKey` obtained during app registration.

3. **Handle Redirects**:
- If the user is already logged in to Ziqx Auth, they will be redirected to the registered redirect URL specified during app registration.
- If the user is not logged in, they will be prompted to authenticate using Ziqx Auth.
- Upon successful authentication, the user will be redirected to the registered redirect URL with a `code` query parameter containing a JWT token with valid user details required for authentication.

## Next Steps

Once you receive the JWT token in the `code` query parameter, you can extract the user details and authenticate the user in your app or website.

