---
description: 'Login, Register, Forget Password'
---

# Authentication

DashboardKit have multiple variants of authentication. It comes with 3 different option to choose.

## How does it work?

Only authenticated users can access dashboard pages. If a user is not authenticated, the user redirected to the login page.

We used two guards **`GuestGuard`** and **`AuthGuard`** . Guards have been configured in **`src\utils\route-guard\`** folder.

In the **`src/layout/App.js`**, we have specified auth provider **`FirebaseProvider`** like,

{% code title="App.js" %}
```javascript
import { FirebaseProvider } from "../contexts/FirebaseContext";
```
{% endcode %}

