---
description: Quick start your project using DashboardKit.
---

# Quick Start

## Installation

Navigate to your root folder **`(i.e. dashboard-kit-react)`**

```text
c:\>cd dashboard-kit-react
```

Install Packages by **npm** or **yarn** as per your preferences. Here we are using **`yarn`** package manager.

```bash
c:\dashboard-kit-react> yarn
```

## Start

After package installation, you can start your app by using **`yarn start`** command

```bash
c:\dashboard-kit-react> yarn start
```

This will start your local server at **`http://localhost:3000`** Also, your terminal shows the following.

```javascript
Compiled successfully!

You can now view dashboard-kit-react in the browser.

Local:            http://localhost:3000
On Your Network:  http://192.168.29.77:3000

Note that the development build is not optimized.
To create a production build, use yarn build.
```

{% hint style="warning" %}
Dashboard-Kit is a vast theme with many components, so it will take little time when you run it first time. Please do not stop execution if it takes time on first launch.
{% endhint %}

## Build & Deploy

This might be too early to deploy but it is always good to know how to deploy.

To build your app in production use **`yarn build`** command

```javascript
c:\DashboardKit-material-react> yarn build
or
c:\DashboardKit-material-react> npm run build
```

## Deploy for your live site

Change the base URL with your domain and build your application.

You can control this with the `homepage` field in your **`package.json`**

{% code title="package.json" %}
```javascript
"homepage" : "http://example.com"
```
{% endcode %}

To deploy it for **subdirectory** `i.e http://example.com/subdirectory/`

{% code title="package.json" %}
```javascript
"homepage" : "http://example.com/subdirectory/"
```
{% endcode %}

You also need to set base-name in **`config.js`** at `'../src/config/'`

{% code title="config.js" %}
```javascript
basename: "/subdirectory";
```
{% endcode %}

{% hint style="info" %}
**You’ll need to have Node v12.x.x or later on your local development machine** \(but it’s not required on the server\). You can use [nvm](https://github.com/creationix/nvm#installation) \(macOS/Linux\) or [nvm-windows](https://github.com/coreybutler/nvm-windows#node-version-manager-nvm-for-windows) to easily switch Node versions between different projects.
{% endhint %}

