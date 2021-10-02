---
description: Page and URL routing
---

# Routing

DashboardKit routing system is based on [react-router](https://reacttraining.com/react-router/) and its package [react-router-dom,](https://reacttraining.com/react-router/web/guides/quick-start) it's also using code splitting for better performance.

{% hint style="info" %}
**How can I add a new page with a menu item?**

You can use the below explanation to add/remove menu routes and their menu items.
{% endhint %}

## Configure route

Open**`...\src\routes\index.js`**You will find the below example code. In the below code we have shown four different routes. **`<MainRoutes/>`** is the main layout routing you see after login.

{% tabs %}
{% tab title="\\routes\\index.js" %}

```javascript
import React, { Suspense } from "react";
import { Redirect, Switch } from "react-router-dom";
import { AnimatePresence } from "framer-motion";

import config from "./../config";
import MainRoutes from "./MainRoutes";
import LoginRoutes from "./LoginRoutes";

import Loader from "../ui-component/extended/Loader/Loader";

import AuthenticationRoutes from "./AuthenticationRoutes";
import DocsRoutes from "./DocsRoutes";

const Routes = () => {
  return (
    <AnimatePresence>
      <Suspense fallback={<Loader />}>
        <Switch>
          <Redirect exact from="/" to={config.defaultPath} />
          <>
            {/* Routes for authetication pages */}
            <AuthenticationRoutes />

            {/* Routes for documentation pages */}
            <DocsRoutes />

            {/* Route for login */}
            <LoginRoutes />

            {/* Routes for main layouts */}
            <MainRoutes />
          </>
        </Switch>
      </Suspense>
    </AnimatePresence>
  );
};

export default Routes;
```

{% endtab %}
{% endtabs %}

### Add New menu/route in the main layout

To add one more menu item in ``**`<MainRoutes />`**, update the following file at the same location **`...\src\routes\MainRoutes.js`\*\*

{% code title="MainRoutes.js" %}

```javascript
...
...
const SamplePage = lazy(() => import('../views/sample-page'));
// import new view and save it in constant. for e.g
const NewMenu = lazy(() => import('../views/new-menu'));

const MainRoutes = () => {
    const location = useLocation();

    return (
        <Route
            path={[
                ...
                ...
                '/sample-page',
                '/new-menu' // add new path like this
            ]}
        >
            <MainLayout showBreadcrumb={true}>
                <Switch location={location} key={location.pathname}>
                    <AuthGuard>
                        ...
                        ...
                        <Route path="/sample-page" component={SamplePage} />
                        // add new route after this. like below
                        <Route path="/new-menu" component={NewMenu} />
                    </AuthGuard>
                </Switch>
            </MainLayout>
        </Route>
    );
};

export default MainRoutes;

```

{% endcode %}

{% hint style="warning" %}
Any route added in **`<MainLayout>`** will automatically go through**`<AuthGuard>`**
{% endhint %}
