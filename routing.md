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

Open**`...\src\routes\route.tsx`**You will find the below example code. In the below code we have shown four different routes.

{% tabs %}
{% tab title="typescript" %}
{% code title="src\routes\routes.tsx" %}
```javascript
import { lazy } from 'react';

// third party
import { Redirect } from 'react-router-dom';

// project imports
import AdminLayout from 'layouts/AdminLayout';
import { BASE_URL } from 'config/constant';

// -----------------------|| Routes ||-----------------------//
const routes = [
    {
        exact: true,
        path: '/404',
        component: lazy(() => import('../views/errors/NotFound404'))
    },
    ...
    ...
    {
        path: '*',
        layout: AdminLayout,
        routes: [
            {
                exact: true,
                path: '/dashboard/sales',
                component: lazy(() => import('../views/dashboard/DashSales'))
            },
            {
                exact: true,
                path: '/dashboard/analytics',
                component: lazy(() => import('../views/dashboard/DashAnalytics'))
            },
            ...
            ...
            {
                path: '*',
                exact: true,
                component: () => <Redirect to={BASE_URL} />
            }
        ]
    }
];

export default routes;
```
{% endcode %}
{% endtab %}
{% endtabs %}
