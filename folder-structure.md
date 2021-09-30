---
description: >-
  Simple intuitive folder structure helps you to navigate easily without any
  hassle.
---

# Folder Structure

Under **`dashboard-kit-react/`** directory, You will find the following folder structure.

{% tabs %}
{% tab title="Folder Structure" %}
```javascript
DashboardKit-material-react
..
├── package.json           -> Package json file.
├── public
├── README.md
├── src
│   ├── _mockApis          -> Mock Json data to be used for working apps
│   ├── assets
│   │   └── images
│   │   └── scss           -> Template SCSS files
│   │       ├── style.scss -> Application main file
│   │       └── _themes-vars.module.scss
│   ├── contexts           -> State context for Login management
│   ├── hooks              -> Custom hooks
│   ├── layout
│   │   ├── DocsLayout     -> Layout for docs components & routers
│   │   ├── MainLayout     -> Layout for main components & routers
│   │   ├── MinimalLayout  -> Layout for mimimal components & routers
│   │   ├── NavigationScroll.js
│   │   └── NavMotion.js
│   ├── menu-items.js      -> menu data
│   ├── routes             -> different route based on layouts
│   ├── store              -> Redux actions, reducers
│   ├── themes             -> Contains application style and theme
│   ├── ui-component       -> Template custom components
│   ├── utils
│   │   ├── locales        -> different locale json files
│   │   ├── route-guard    -> Auth guard to prevent unexpected navigations
│   └── views              -> View files for all pages
├── App.js                 -> starting point of application
├── config.js              -> Template constant value and live customization
├── index.js               -> Application root js file
```
{% endtab %}
{% endtabs %}

