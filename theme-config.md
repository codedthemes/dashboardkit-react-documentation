---
description: Defines core of theme. How theme is being set using Material-UI.
---

# Theme/Style Configuration

Customize Material-UI with your theme. You can change the colors, the typography, and much more. Material-UI provides flexibility to change the style of the project in a single place and on top of it, we made it more centralize and consistent by proper file structure.

## Theme configuration

The Entire theme can be configured from the folder **`..\src\themes`** . Theme initialization starts in**`index.js`** , where palette, typography, and component's overridable style exist.

{% code title="index.js" %}
```javascript
import {createTheme} from '@material-ui/core/styles';
import value from '../assets/scss/_themes-vars.module.scss'; // central place for all colors
import {componentStyleOverrides} from './compStyleOverride';
import {themePalatte} from './palatte';
import {themeTypography} from './typography';

export function theme(customization) {
    let navObject = {
        heading: '',
        paper: '',
        backgroundDefault: '',
        background: '',
        textDarkPrimary: '',
        textDarkSecondary: '',
        textDark: '',
        menuSelected: '',
        menuSelectedBack: '',
        divider: '',
        customization: customization
    };

    switch (customization.navType) {
        case 'dark':
            navObject.paper = value.darkLevel2;
            navObject.backgroundDefault = value.paperDark;
            navObject.background = value.backgroundDark;
            navObject.textDarkPrimary = value.textDarkPrimary;
            navObject.textDarkSecondary = value.textDarkSecondary;
            navObject.textDark = value.textDarkPrimary;
            navObject.menuSelected = value.blue500;
            navObject.menuSelectedBack = value.darkLevel1;
            navObject.divider = value.textDarkPrimary;
            navObject.heading = value.textDarkTitle;
            break;
        case 'light':
        default:
            navObject.paper = value.paper;
            navObject.backgroundDefault = value.paper;
            navObject.background = value.blue50;
            navObject.textDarkPrimary = value.grey700;
            navObject.textDarkSecondary = value.grey500;
            navObject.textDark = value.grey900;
            navObject.menuSelected = value.deepPurple600;
            navObject.menuSelectedBack = value.blue50;
            navObject.divider = value.grey200;
            navObject.heading = value.grey900;
            break;
    }

    return createTheme({
        direction: customization.rtlLayout ? 'rtl' : 'ltr', // theme direction
        palette: themePalatte(navObject), // color palatte
        mixins: {
            toolbar: {
                minHeight: '48px',
                padding: '16px',
                '@media (min-width: 600px)': {
                    minHeight: '48px'
                }
            }
        },
        typography: themeTypography(navObject), // typography
        components: componentStyleOverrides(navObject) // overrided component style
    });
}

export default theme;

```
{% endcode %}

As you can see colors for the theme came from the central location ``**`import value from '../assets/scss/_themes-vars.module.scss';`**

```css
// Paper & Background Color
$paper: #ffffff;
$background: #ffffff;

// Primary Colors
$blue50: #e3f2fd;
...

// Success Colors
$A100: #b9f6ca;
..

// Purple Colors
$deepPurple50: #ede7f6;
...

// Error Colors
$red200: #ef9a9a;
...

// Orange Colors
$deepOrange50: #fbe9e7;
...

// Warning Colors
$amber50: #fff8e1;
...

// Grey Colors
$grey50: #fafafa;
...

// Dark Theme Variants

$darkLevel1: #29314f;
...

$textDarkTitle: #d7dcec;
...

// this will use in javascript
:export {
    paper: $paper;
    ...

    darkLevel1: $darkLevel1;
    ...

    blue50: $blue50;
    ...

    A100: $A100;
    ...

    deepPurple50: $deepPurple50;
    ...

    amber50: $amber50;
    ...

    grey50: $grey50;
    ...
    red200: $red200;
    ...

    deepOrange50: $deepOrange50;
    ...
}

```

You can check other settings like theme typography, palette, and components style override in the same folder. **`..src\themes`**

### How to customize it?

You might come across questions like how to change a theme's **primary** color? How to change textbox or other components which can apply to an entire theme?  

#### Customize Theme Colors

To change the color of the theme, you can either apply color directly to `..src\theme\palatte.js` **or** defines a new variable in `..src\assets\scss\_themes-vars.module.scss` and replace it in `palatte.js`

For instance, if you want to change color where `theme.palette.primary.light` is being used in a theme then, update following in **`..src\themes\palatte.js`**

{% code title="palatter.js" %}
```javascript
import value from '../assets/scss/_themes-vars.module.scss';

/**
 * Color intention that you want to used in your theme
 */
export function themePalatte(theme) {
    return {
        ...
        primary: {
            light: '#fff000', // change this to your desired color
            ...
        },
        ...
        ...

    };
}

```
{% endcode %}

#### Customize Theme Typography

You can customize the typography used in the theme as well from the central place.

For instance, If you want to change `font-weight` of the typography `h5` to `900`. To do that, open **`..src\themes\typography.js`** and update as below:

{% code title="typography.js" %}
```javascript
/**
 * Typography used in theme
 */
export function themeTypography(theme) {
    return {
        ...
        h5: {
            ...
            fontWeight: 900 // changed this to make it 900 from 500
        },
        ...
    };
}

```
{% endcode %}

This will apply to all places where you used Typography variant as **`h5`**

**`<Typography variant="h5"...>`**

#### Customize MUI Component style

We have provided a central location to override any default style of any component. All the overrides style exist in **`src\themes\compStyleOverride.js`**

{% code title="compStyleOverride.js" %}
```javascript
import value from '../assets/scss/_themes-vars.module.scss';

/**
 * MUI Componets whose styles are overrided as per theme
 */
export function componentStyleOverrides(theme) {
    return {
        MuiButton: {
            styleOverrides: {
                root: {
                    fontWeight: 500,
                    textTransform: 'capitalize',
                    borderRadius: '4px'
                }
            }
        },
        ...
        ...
        MuiDialog: {
            styleOverrides: {
                paper: {
                    padding: '12px 0 12px 0'
                }
            }
        }
    };
}

```
{% endcode %}

You can add default property for any MUI component and it will be applied everywhere. We emitted lines to view it better in the above code block but you can see many controls' styles override in the same file. Feel free to change it as per your need.

