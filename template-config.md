# Template Config

{% hint style="info" %}
You can edit this file at **`[ ../src/config.js ]`**
{% endhint %}

| **Option** | **Default** | **Data Type** | **Description** |
| :--- | :--- | :--- | :--- |
| **basename** | / | String | `build time set subdomain or path of project directory` |
| **theme** | light | String | `light, dark, nav-dark` |
| **jwt** | - | Object | JSON web token configuration |
| **firebase** | - | Object | `Firebase Authentication config` |
| **auth0** | - | Object | `auth0 login config` |

{% tabs %}
{% tab title="config.js" %}
```javascript
export default {
    basename: '/material-ui', // only at build time to set, like ///able-pro/react/default
    theme: 'light', // 'light', 'dark', 'nav-dark'
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

