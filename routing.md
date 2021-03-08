# Routing

This Template routing system based on [react-router](https://reacttraining.com/react-router/) and its package [react-router-dom,](https://reacttraining.com/react-router/web/guides/quick-start) it's also using code splitting for better performance.

{% hint style="info" %}
**How can I add a new page with a menu item?**

You can use the below explanation to add/remove menu routes and their menu items.
{% endhint %}

## Configure route

Open`materially/src/Routes.js`You will find the below example code. In the below code we have shown how you can add a new page route.

{% tabs %}
{% tab title="router.js" %}
```javascript
import React, { lazy, Suspense } from 'react';
import { Switch, Route, Redirect, useLocation } from 'react-router-dom';
import { AnimatePresence } from 'framer-motion';

import Loader from './component/Loader/Loader';
import NavMotion from './layout/NavMotion';
import MainLayout from './layout/MainLayout';
import GuestGuard from "./component/Auth/GuestGuard";
import AuthGuard from "./component/Auth/AuthGuard";
import MinimalLayout from "./layout/MinimalLayout";

const AuthLogin = lazy(() => import('./views/Login'));

const DashboardDefault = lazy(() => import('./views/Dashboard/Default'))
const SamplePage = lazy(() => import('./views/SamplePage'));

const Routes = () => {
    const location = useLocation();

    return (
        <AnimatePresence>
            <Suspense fallback={<Loader />}>
                <Switch>
                    <Redirect exact from="/" to="/dashboard/default" />
                    <Route path={['/login']}>
                        <MinimalLayout>
                            <Switch location={location} key={location.pathname}>
                                <NavMotion>
                                    <GuestGuard>
                                        <Route path="/login" component={AuthLogin} />
                                    </GuestGuard>
                                </NavMotion>
                            </Switch>
                        </MinimalLayout>
                    </Route>
                    <Route
                        path={[
                        '/dashboard/default',
                        '/sample-page'
                    ]}>
                        <MainLayout>
                            <Switch location={location} key={location.pathname}>
                                <NavMotion>
                                    <AuthGuard>
                                        <Route path="/dashboard/default" component={DashboardDefault} />
                                        <Route path="/sample-page" component={SamplePage} />
                                    </AuthGuard>
                                </NavMotion>
                            </Switch>
                        </MainLayout>
                    </Route>
                </Switch>
            </Suspense>
        </AnimatePresence>
    );
};

export default Routes;

```
{% endtab %}
{% endtabs %}

## Add menu item

To add menu items you can use file `materially/src/menu-items.js`. In the below code, we have shown how you can use a new menu item.

{% tabs %}
{% tab title="menus.js" %}
```javascript
import NavigationOutlinedIcon from '@material-ui/icons/NavigationOutlined';
import HomeOutlinedIcon from '@material-ui/icons/HomeOutlined';
import CardGiftcardOutlinedIcon from '@material-ui/icons/CardGiftcardOutlined';

const icons = {
    NavigationOutlinedIcon: NavigationOutlinedIcon,
    HomeOutlinedIcon: HomeOutlinedIcon,
    CardGiftcardOutlinedIcon: CardGiftcardOutlinedIcon
};

export default {
    items: [
        {
            id: 'navigation',
            title: 'Navigation',
            caption: 'Theme Analysis',
            type: 'group',
            icon: icons['NavigationOutlinedIcon'],
            children: [
                {
                    id: 'dashboard',
                    title: 'Dashboard',
                    type: 'item',
                    icon: icons['HomeOutlinedIcon'],
                    url: '/dashboard/default'
                },
            ]
        },                
        {
            id: 'support',
            title: 'Support',
            type: 'group',
            icon: icons['ContactSupportOutlinedIcon'],
            children: [
                {
                    id: 'menu-level',
                    title: 'Menu Levels',
                    type: 'collapse',
                    icon: icons['LayersOutlinedIcon'],
                    children: [
                        {
                            id: 'menu-level-1.1',
                            title: 'Level 1',
                            type: 'item',
                            url: '#!',
                        },
                        {
                            id: 'menu-level-1.2',
                            title: 'Level 1',
                            type: 'collapse',
                            children: [
                                {
                                    id: 'menu-level-2.1',
                                    title: 'Level 2',
                                    type: 'item',
                                    url: '#',
                                },
                                {
                                    id: 'menu-level-2.2',
                                    title: 'Level 2',
                                    type: 'collapse',
                                    children: [
                                        {
                                            id: 'menu-level-3.1',
                                            title: 'Level 3',
                                            type: 'item',
                                            url: '#',
                                        },
                                        {
                                            id: 'menu-level-3.2',
                                            title: 'Level 3',
                                            type: 'item',
                                            url: '#',
                                        }
                                    ]
                                }
                            ]
                        }
                    ]
                },
                {
                    id: 'menu-level-subtitle',
                    title: 'Sub Cation Levels',
                    caption: 'Caption Collapse',
                    type: 'collapse',
                    icon: icons['LayersOutlinedIcon'],
                    children: [
                        {
                            id: 'sub-menu-level-1.1',
                            title: 'Level 1',
                            caption: 'Caption Item',
                            type: 'item',
                            url: '#!',
                        },
                        {
                            id: 'sub-menu-level-1.2',
                            title: 'Level 1',
                            caption: 'Sub Collapse Caption',
                            type: 'collapse',
                            children: [
                                {
                                    id: 'sub-menu-level-2.1',
                                    title: 'Level 2',
                                    caption: 'Sub Item Caption',
                                    type: 'item',
                                    url: '#',
                                }
                            ]
                        }
                    ]
                },
                {
                    id: 'disabled-menu',
                    title: 'Disabled Menu',
                    type: 'item',
                    url: '#',
                    icon: icons['BlockOutlinedIcon'],
                    disabled: true
                },
                {
                    id: 'sample-page',
                    title: 'Sample Page',
                    caption: 'Skeleton Page',
                    type: 'item',
                    url: '/sample-page',
                    icon: icons['ChromeReaderModeOutlinedIcon']
                }
            ]
        }
    ]
}

```
{% endtab %}
{% endtabs %}

