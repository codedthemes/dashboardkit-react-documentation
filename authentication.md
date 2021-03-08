---
description: Materially supports 3 popular Authentication methods.
---

# Authentication

Materially supports 3 authentication methods:  **Firebase Authentication, JSON Web Token, Auth0**.

**FYI** - We provide Firebase Authentication by default.

## How does it work?

Only authenticated users can access dashboard pages. If a user is not authenticated, the user redirected to the login page.

We implemented to make this work the “Guard” concept from Angular. It is simply a component that wraps a route and checks for user authentication status before allowing the navigation. 

We used two guards **GuestGuard** and **AuthGuard**, To find more information about guards, please visit the **Routes.js** page.

 In the `src/layout/App.js`,  we have specified  auth provider **FirebaseProvider** like,

```text
import { FirebaseProvider } from "../contexts/FirebaseContext";
```

App component wrap with the provider, like

```text
<ThemeProvider theme={theme(customization)}>
  <FirebaseProvider>
    <Routes />
    <Snackbar />
  </FirebaseProvider>
</ThemeProvider>
```

 Using **FirebaseProvider**, we can use the context directly by importing `useContext` from React and specifying the context **FirebaseContext** that we want to use or we can use the custom hook **`useAuth`** from `src/hooks/useAuth.js`

## Auth Configuration:

{% hint style="info" %}
You can edit this file at **`[ ../src/config.js]`**
{% endhint %}

```text
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

###  <a id="switching-between-auth-methods"></a>

## Switching between Authentication methods

### **Firebase to JWT**

**Set JWT Config** - Open file '**config.js**' at directory '../src/config.js' and set **jwt** configuration.

```text
export default {
	...
	jwt: {
      secret: 'SECRET-KEY',
      timeout: '1 days'
  }
}
```

**Change Login Form** - Open file '**index.js**' at directory '../src/views/Login/index.js', and use the **JWTLogin** component.

```text
// Replace at line 8:
import JWTLogin from './JWTLogin';

// Replace at line 21: 
<JWTLogin />
```

**AuthProvider for Layout** - Open file '**App.js**' at directory '../src/layout/App.js' and use **JWTProvider**

```text
// Replace at line 6;
import { JWTProvider } from "./contexts/JWTContext";

// Replace from line 22:
<JWTProvider>
    <Routes />
    <Snackbar />
</JWTProvider>
```

 **Change auth Hooks** - Open file '**useAuth.js**' at directory '../src/hooks/useAuth.js' and use **JWTContext**

```text
// Replace from line 2:
import JWTContext from '../contexts/JWTContext';
const useAuth = () => useContext(JWTContext);
```

### \*\*\*\*

### **Firebase to Auth0**

**Set Auth Config** - Open file '**config.js**' at directory '../src/config.js' and set **auth0** configuration.

```text
export default {
	...
	auth0: {
		client_id: 'CLIENT-ID',
		domain: 'DOMAIN'
  }
}
```

**Change Login Form** - Open file '**index.js**' at directory '../src/views/Login//index.js', and use **Auth0Login** component.

```text
// Replace at line 8:
import Auth0Login from './Auth0Login';

// Replace at line 21: 
<Auth0Login />
```

**AuthProvider for Layout** - Open file '**App.js**' at directory '../src/layout/App.js' and use **Auth0Provider**

```text
// Replace at line 6;
import { Auth0Provider } from "./contexts/Auth0Context";

// Replace from line 22:
<Auth0Provider>
    {renderRoutes(routes)}
</Auth0Provider>
```

 **Change auth Hooks** - Open file '**useAuth.js**' at directory '../src/hooks/useAuth.js' and use **Auth0Context**

```text
// Replace from line 2:
import Auth0Context from '../contexts/Auth0Context';
const useAuth = () => useContext(Auth0Context);
```

