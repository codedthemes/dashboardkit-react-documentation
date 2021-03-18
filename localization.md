---
description: >-
  Localization support IE11 & 2 most recent versions of Edge, Chrome, Firefox &
  Safari.
---

# Localization

React Intl has a set of React components that provide a declarative way to setup an i18n context and format dates, numbers, and strings for display in a web UI. The components render React elements by building on React Intl's imperative [API](https://formatjs.io/docs/react-intl/api).

## IntlProvider

 React Intl uses the provider pattern to scope an i18n context to a tree of components. This allows configuration like the current locale and set of translated strings/messages to be provided at the root of a component tree and made available to the `<Formatted*>` components. This is the same concept as what Flux frameworks like [Redux](http://redux.js.org/) use to provide access to a store within a component tree.

## locale, formats, and messages

 The user's current locale and what the app should be rendered in. While `defaultLocale` and `defaultFormats` are for fallbacks or during development and represent the app's default. Notice how there is no, `defaultMessages`, that's because each [Message Descriptor](https://formatjs.io/docs/react-intl/components#message-descriptor) provides a `defaultMessage`

## How does it work?

1. Add node modules `react-intl` emo

   ```text
   yarn add react-intl / npm install --save react-intl
   ```

2. Create language file `language-code.json` at directory '**../src/compiled-lang**'. 

   ```text
   {
       "title": "Multi Language",
       "home": "Home",
       "change": "Change Language",
       "message": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiatnulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollitanim id est laborum."
   }
   ```

3. Open file `config.js` file and set language.

   ```text
   export default {
       ...
       i18n: 'en'
       ...
   }
   ```

4. Open file `App.js` and apply **IntlProvider**

   ```text
   import { IntlProvider } from 'react-intl';

   function loadLocaleData(locale) {
       switch (locale) {
         case 'fr':
           return import('./../compiled-lang/fr.json');
         case 'ro':
           return import('./../compiled-lang/ro.json');
         case 'cn':
           return import('./../compiled-lang/cn.json');
         default:
           return import('./../compiled-lang/en.json');
       }
   }

   const App = () => {
       const customization = useSelector((state) => state.customization);
       const [messages, setMessages] = useState();

       useEffect(() => {
           loadLocaleData(customization.locale).then(d=>{
               setMessages(d.default);
           });
       }, [customization]);

       return (
           <React.Fragment>
           { messages && <IntlProvider
               locale='fr'
               defaultLocale="en"
               messages={messages}
               >
               ...
               ...
               ...
           </IntlProvider> }
           </React.Fragment>
       );
   };

   export default App;

   ```





