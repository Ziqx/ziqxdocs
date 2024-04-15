---
sidebar_position: 3
---

# WhatsApp Login

WhatsApp Login allows users to authenticate using WhatsApp. It provides a straightforward authentication process where users receive a login link via WhatsApp. Upon successful authentication, the user is redirected to the registered URL.

## Prerequisites

To use WhatsApp Login with Ziqx Auth, the following prerequisites must be met:

1. Your app must be verified and approved for WhatsApp Login by Ziqx Auth.
2. You must have the Ziqx Auth WhatsApp number (`ziqx_auth_wp_number`) provided by Ziqx Auth.

## Implementation Steps
1. **Generate WhatsApp Login Link**:
   Create a login link using the following format:
   ```
   https://wa.me/{ziqx_auth_wp_number}?text=Login%20to%20{APP_NAME}
   ```
Replace `{ziqx_auth_wp_number}` with the Ziqx Auth WhatsApp number, and `{APP_NAME}` with your app name.

2. **Redirect users to the above link**:
Redirect users to the above link. Once the user sends the message he/she will get a unique url with auth code. Once the user opens the link he/she will be authenticated.

3. **Redirect Upon Authentication**:
Upon successful authentication, the user will be redirected to the registered URL specified during app registration.

## Note

- WhatsApp Login is limited to verified apps only. Contact Ziqx Auth support to request verification for your app.

- All login methods, including WhatsApp Login, are accessible if you are using redirect login, as the authentication process occurs on the Ziqx Auth website.

## Example

Here's an example of how to generate a WhatsApp login link in JavaScript:

```javascript
const ziqxAuthWpNumber = "1234567890"; // Replace with your Ziqx Auth WhatsApp number
const appName = "YourApp"; // Replace with your app name

const whatsappLoginLink = `https://wa.me/${ziqxAuthWpNumber}?text=Login%20to%20${appName}`;

console.log(whatsappLoginLink);
```

HTML Template
```html
<a href="https://wa.me/{ziqxAuthWpNumber}?text=Login%20to%20{appName}">Login with WhatsApp</a>
```