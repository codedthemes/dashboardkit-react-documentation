---
description: Configuration option for whole DashboardKit Template
---

# Project Configuration

DashboardKit has a single source of truth for default configuration which lets users manage it effectively. It also makes it scalable for new configurations. you can set config like font, border, theme layout, locale, etc. All those can be configured at **`..src/config.js`**

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>Option</b>
      </th>
      <th style="text-align:left"><b>Default</b>
      </th>
      <th style="text-align:left"><b>Data Type</b>
      </th>
      <th style="text-align:left"><b>Description</b>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>basename</b>
      </td>
      <td style="text-align:left">/</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left"><code>build time set subdomain or path of project directory</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>defaultPath</b>
      </td>
      <td style="text-align:left">/dashboard/default</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">default path once login success</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>fontFamily</b>
      </td>
      <td style="text-align:left">&apos;Roboto&apos;, sans-serif</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">set font family</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>borderRadius</b>
      </td>
      <td style="text-align:left">12</td>
      <td style="text-align:left">number</td>
      <td style="text-align:left">border-radius for card and textboxes</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>outlinedFilled</b>
      </td>
      <td style="text-align:left">true</td>
      <td style="text-align:left">boolean</td>
      <td style="text-align:left">defines backfill color for textboxes. setting it false will show transparent
        background for outline textboxes</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>theme</b>
      </td>
      <td style="text-align:left">light</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left"><code>light, dark</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>18n</b>
      </td>
      <td style="text-align:left">en</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">
        <p><code>en</code> - English</p>
        <p><code>fr</code> - fran&#xE7;ais</p>
        <p><code>ro</code> - Rom&#xE2;n&#x103;</p>
        <p><code>zh</code> - &#x4E2D;&#x56FD;&#x4EBA;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>rtlLayout</b>
      </td>
      <td style="text-align:left">false</td>
      <td style="text-align:left">boolean</td>
      <td style="text-align:left">set layout from right to left.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>jwt</b>
      </td>
      <td style="text-align:left">-</td>
      <td style="text-align:left">Object</td>
      <td style="text-align:left">JSON web token configuration</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>firebase</b>
      </td>
      <td style="text-align:left">-</td>
      <td style="text-align:left">Object</td>
      <td style="text-align:left"><code>Firebase Authentication config</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>auth0</b>
      </td>
      <td style="text-align:left">-</td>
      <td style="text-align:left">Object</td>
      <td style="text-align:left"><code>auth0 login config</code>
      </td>
    </tr>
  </tbody>
</table>

{% tabs %}
{% tab title="config.js" %}

```javascript
const config = {
  // basename: only at build time to set, and don't add '/' at end off BASENAME for breadcrumbs,  like '/DashboardKit-material-react/react/default'
  basename: "/",
  defaultPath: "/dashboard/default",
  fontFamily: `'Roboto', sans-serif`,
  borderRadius: 12,
  outlinedFilled: true,
  theme: "light",
  i18n: "en", // 'en' - English, 'fr' - French, 'ro' - Romanian, 'zh' - Chinese
  rtlLayout: false,
  jwt: {
    secret: "SECRET-KEY",
    timeout: "1 days",
  },
  firebase: {
    apiKey: "apiKey",
    authDomain: "authDomain",
    projectId: "DashboardKit-material-react",
    storageBucket: "DashboardKit-material-react.appspot.com",
    messagingSenderId: "messagingSenderId",
    appId: "appId",
    measurementId: "measurementId",
  },
  auth0: {
    client_id: "client_id",
    domain: "demo-localhost.us.auth0.com",
  },
};

export default config;
```

{% endtab %}
{% endtabs %}
