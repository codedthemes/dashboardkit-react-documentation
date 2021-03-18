# Template Config

{% hint style="info" %}
You can edit this file at **`[ ../src/config.js ]`**
{% endhint %}

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
      <td style="text-align:left"><b>theme</b>
      </td>
      <td style="text-align:left">light</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left"><code>light, dark, nav-dark</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>rtlLayout</b>
      </td>
      <td style="text-align:left">false</td>
      <td style="text-align:left">boolean</td>
      <td style="text-align:left"><code>false, true</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>i18n</b>
      </td>
      <td style="text-align:left">en</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">
        <p><code>en</code> - English</p>
        <p><code>fr</code> - fran&#xE7;ais</p>
        <p><code>ro</code> - Rom&#xE2;n&#x103;</p>
        <p><code>cn</code> - &#x4E2D;&#x56FD;&#x4EBA;</p>
      </td>
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
export default {
    basename: '/material-ui', // only at build time to set, like ///materially/react/default
    theme: 'light', // 'light', 'dark', 'nav-dark'
    rtlLayout: false,
    i18n: 'en', // 'en', 'fr', 'ro', 'cn'
    jwt: {
        secret: 'SECRET-KEY',
        timeout: '1 days'
    },
    firebase: {
        apiKey: "AIzaSyA5JDOpLrxMl_RBKI37tgI3ru4Mf0b0IZU",
        authDomain: "mui-new.firebaseapp.com",
        databaseURL: "https://mui-new.firebaseio.com",
        projectId: "mui-new",
        storageBucket: "mui-new.appspot.com",
        messagingSenderId: "613731531365",
        appId: "1:613731531365:web:8fb076dea33bf5b606a48c",
        measurementId: "G-PCJ3C8RCN2"
    },
    auth0: {
        client_id: 'HvYn25WaEHb7v5PBT7cTYe98XATStX3r',
        domain: 'demo-localhost.us.auth0.com'
    }
}


```
{% endtab %}
{% endtabs %}

