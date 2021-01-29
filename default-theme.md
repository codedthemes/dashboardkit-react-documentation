# Default Theme

Customize Material-UI with your theme. You can change the colors, the typography, and much more.

### Theme configuration variables

Changing the theme configuration variables is the most effective way to match Material-UI to your needs. The following sections cover the most important theme variables:

* [Palette](https://material-ui.com/customization/palette/)
* [Typography](https://material-ui.com/customization/typography/)
* [Spacing](https://material-ui.com/customization/spacing/)
* [Breakpoints](https://material-ui.com/customization/breakpoints/)
* [z-index](https://material-ui.com/customization/z-index/)
* [Globals](https://material-ui.com/customization/globals/)

You can check out the [default theme section](https://material-ui.com/customization/default-theme/) to view the default theme in full.

**Examples**

```text
import { createMuiTheme } from '@material-ui/core/styles';
import purple from '@material-ui/core/colors/purple';
import green from '@material-ui/core/colors/green';

const theme = createMuiTheme({
  palette: {
    primary: {
      main: purple[500],
    },
    secondary: {
      main: green[500],
    },
  },
});
```

{% hint style="info" %}
You can edit this file at **`[ ../src/themes/index.js]`**
{% endhint %}

```text
import { createMuiTheme } from '@material-ui/core';
import value from '../assets/scss/_themes-vars.scss';
import grey from '@material-ui/core/colors/grey';


export function theme(customization) {
    switch(customization.navType) {
        case 'dark':
            ...
        case 'nav-dark':
            ...
        case 'light':
        default:
            ...
    }

    return createMuiTheme({
        palette: {
            ...
        },
        typography: {
            fontFamily: `'Inter', sans-serif`,
            ....
        },
        breakpoints: {
            values: {
                xs: 0,
                sm: 600,
                md: 960,
                lg: 1280,
                xl: 1920,
                mobile: 430
            }
        },
        overrides: {
            ...
        },
    });
};

export default theme;

```

If you want to learn more about how the theme is assembled, take a look at [`material-ui/style/createMuiTheme.js`](https://github.com/mui-org/material-ui/blob/master/packages/material-ui/src/styles/createMuiTheme.js), and the related imports which `createMuiTheme` uses.

