---
description: "Auth0, JWT, Firebase setup"
---

# Authentication

DashboardKit supports three Authentication methods **`Firebase, JSON Web Token (JWT), Auth0.`**

{% hint style="info" %}
Firebase Authentication set by default
{% endhint %}

## How does it work?

Only authenticated users can access dashboard pages. If a user is not authenticated, the user redirected to the login page.

We used two guards **`GuestGuard`** and **`AuthGuard`** . Guards have been configured in **`src\utils\route-guard\`** folder.

In the **`src/layout/App.js`**, we have specified auth provider **`FirebaseProvider`** like,

{% code title="App.js" %}

```javascript
import { FirebaseProvider } from "../contexts/FirebaseContext";
```

{% endcode %}

App component wrap with the **`<FirebaseProvider>`**

```javascript
<ThemeProvider theme={theme(customization)}>
  <FirebaseProvider>
    <Routes />
    <Snackbar />
  </FirebaseProvider>
</ThemeProvider>
```

Using **`<FirebaseProvider>`**, we can use the context directly by importing **`useContext`** from React and specifying the context **`FirebaseContext`** or we can use the custom hook **`useAuth`** from `src/hooks/useAuth.js`

## Auth Configuration:

{% hint style="info" %}
You can edit this file at **`[ ../src/config.js]`**
{% endhint %}

{% code title="config.js" %}

```javascript
// JWT JSON Web Token method
jwt: {
    secret: 'SECRET-KEY',
    timeout: '1 days'
},

// Firebase Authentication method
firebase: {
    apiKey: "API-KEY",
    authDomain: "AUTH-DOMAIN",
    databaseURL: "DATABASE-URL",
    projectId: "PROJECT-ID",
    storageBucket: "STORAGE-BUCKET",
    messagingSenderId: "MESSAGEING-SENDER-ID",
    appId: "APP-ID",
    measurementId: "MEASUREMENT-ID"
},

// Auth0 method
auth0: {
    client_id: 'CLIENT-ID',
    domain: 'DOMAIN'
}
```

{% endcode %}

## Switching between Authentication methods

### **Firebase to JWT**

**Set JWT Config**

Open file **`config.js`** from directory **`..\src\config.js`** and set **`jwt`** configuration.

{% code title="config.js" %}

```javascript
...
  jwt: {
      secret: 'SECRET-KEY',
      timeout: '1 days'
  }
...
```

{% endcode %}

**Change Login Form**

Open file **`index.js`** at directory **`..\src\views\pages\authentication\login\index.js`** and use the **`JWTLogin`** component.

{% code title="login\\index.js" %}

```javascript
// Replace at line 8:
import JWTLogin from "./JWTLogin";

// Also find & edit below code block
<Grid item xs={12}>
  <JWTLogin />
  {/* <Auth0Login /> */}
  {/* <FirebaseLogin /> */}
</Grid>;
```

{% endcode %}

**Change AuthProvider**

Open file **`App.js`** at directory **`..\src\App.js`** and use **`JWTProvider`**

{% code title="App.js" %}

```javascript
// Replace at line 6:
import { JWTProvider } from "./contexts/JWTContext";

// Also find & edit below code block
<JWTProvider>
  <Routes />
  <Snackbar />
</JWTProvider>;
```

{% endcode %}

**Change auth Hooks**

Open file **`useAuth.js`** at directory `..\src\hooks\useAuth.js` and use **`JWTContext`**

{% code title="useAuth.js" %}

```javascript
// Replace from line 2:
import JWTContext from "../contexts/JWTContext";
const useAuth = () => useContext(JWTContext);
```

{% endcode %}

### **Firebase to Auth0**

**Set Auth0 Config**

Open file **`config.js`** from directory **`..\src\config.js`** and set **`jwt`** configuration.

{% code title="config.js" %}

```javascript
...
  auth0: {
      client_id: 'client_id',
      domain: 'yourdomain.com'
  }
...
```

{% endcode %}

**Change Login Form**

Open file **`index.js`** at directory **`..\src\views\pages\authentication\login\index.js`** and use the **`Auth0Login`** component.

{% code title="\\login\\index.js" %}

```javascript
// Replace at line 8:
import Auth0Login from "./Auth0Login";

// Also find & edit below code block
<Grid item xs={12}>
  {/* <JWTLogin /> */}
  <Auth0Login />
  {/* <FirebaseLogin /> */}
</Grid>;
```

{% endcode %}

**Change AuthProvider**

Open file **`App.js`** at directory **`..\src\App.js`** and use **`Auth0Provider`**

{% code title="App.js" %}

```javascript
// Replace at line 6:
import { Auth0Provider } from "./contexts/Auth0Context";

// Also find & edit below code block
<Auth0Provider>
  <Routes />
  <Snackbar />
</Auth0Provider>;
```

{% endcode %}

**Change auth Hooks**

Open file **`useAuth.js`** at directory **`..\src\hooks\useAuth.js`** and use **`Auth0Context`**

{% code title="useAuth.js" %}

```javascript
// Replace from line 2:
import Auth0Context from "../contexts/Auth0Context";
const useAuth = () => useContext(Auth0Context);
```

{% endcode %}
