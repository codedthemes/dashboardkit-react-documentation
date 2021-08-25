---
description: "Localization support IE11, Edge, Chrome, Firefox & Safari."
---

# Internationalization

DashboardKit supports four types of international languages \('**en**' - English, '**fr**' - French, '**ro**' - Romanian, '**zh**' - Chinese\). You can switch language from the header bar. We internationalize the main menu for all four languages, When you change it from the header, you will see the effect there. If you want to configure one more language or set a default language then continue reading below...

## How does it work?

Data for locale files exist at **`src\utils\locales`**

{% code title=".json file" %}

```javascript
{
    "dashboard": "Dashboard",
    "default": "Default",
    "analytics": "Analytics",
    ...
    ...
}
```

{% endcode %}

To change Locale, open file **`src\config.js`** file and set language

{% code title="config.js" %}

```javascript
const config = {
    ...
    i18n: 'en', // 'en' - English, 'fr' - French, 'ro' - Romanian, 'zh' - Chinese
    ...
}
```

{% endcode %}

Open file **`App.js`** and apply **IntlProvider**

{% code title="App.js" %}

```javascript
import { IntlProvider } from "react-intl";

function loadLocaleData(locale) {
  switch (locale) {
    case "fr":
      return import("./../compiled-lang/fr.json");
    case "ro":
      return import("./../compiled-lang/ro.json");
    case "zh":
      return import("./../compiled-lang/zh.json");
    default:
      return import("./../compiled-lang/en.json");
  }
}

const App = () => {
  const customization = useSelector((state) => state.customization);
  const [messages, setMessages] = useState();

  useEffect(() => {
    loadLocaleData(customization.locale).then((d) => {
      setMessages(d.default);
    });
  }, [customization]);

  return (
    <React.Fragment>
      {messages && (
        <IntlProvider locale="fr" defaultLocale="en" messages={messages}>
          ... ... ...
        </IntlProvider>
      )}
    </React.Fragment>
  );
};

export default App;
```

{% endcode %}
