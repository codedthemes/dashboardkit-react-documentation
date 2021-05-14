# Color Management\_old

The Material Design color system helps you apply color to your UI in a meaningful way. In this system, you select a primary and a secondary color to represent your brand. Dark and light variants of each color can then be applied to your UI in different ways.

{% hint style="info" %}
You can edit this file at **`[ ../src/assets/scss/_themes-vars.scss]`**
{% endhint %}

```text
$primary: #0061f2;
$primary100: #4c6fff;

$primaryDark: #0043a9;
$primaryLight: #3380f4;


$secondary: #425466;
$secondaryDark: #272f33;
$secondaryLight: #60696D;

$error: #e81500;
$errorDark: #a20e00;
$errorLight: #ec4333;

$warning: #f4a100;
$warningDark: #aa7000;
$warningLight: #f6b333;

$info: #00cfd5;
$infoDark: #009095;
$infoLight: #33d8dd;

$success: #00ac69 ;
$successDark: #007849;
$successLight: #33bc87;

$grey300: #425466;
$dark: #343a40;

$bg100: #f8f8f9;

// Text Colors

$textPrimary: #69707a;
$textSecondary: #4a515b;
$textDark: #212832;
$textHint: #00000061;

// Text Dark Color
$textDarkPrimary: #bbc0c7;
$textDarkSecondary: #babfc9;
$textDarkDark: #e3e8ec;
$texDarkHint: #94919161;

// Background Color
$backgound: #f0f2f8;
$backgoundDark: #303030;

// Paper Color
$paper: #ffffff;
$paperDark: #424242;

// this will use in defaultTheme
:export {
    primary: $primary;
    primaryDark: $primaryDark;
    primaryLight: $primaryLight;
    primary100: $primary100;

    secondary: $secondary;
    secondaryDark: $secondaryDark;
    secondaryDark: $secondaryDark;

    error: $error;
    errorDark: $errorDark;
    errorLight: $errorLight;

    warning: $warning;
    warningDark: $warningDark;
    warningLight: $warningLight;

    info: $info;
    infoDark: $infoDark;
    infoLight: $infoLight;

    success: $success;
    successDark: $successDark;
    successLight: $successLight;

    grey300: $grey300;

    bg100: $bg100;

    // Text Colors
    textPrimary: $textPrimary;
    textSecondary: $textSecondary;
    textDark: $textDark;
    textHint: $textHint;

    // Text Dark Colors
    textDarkPrimary: $textDarkPrimary;
    textDarkSecondary: $textDarkSecondary;
    textDarkDark: $textDarkDark;
    textDarkHint: $texDarkHint;

    // Background Color
    backgound: $backgound;
    backgoundDark: $backgoundDark;

    // Paper Color
    paper: $paper;
    paperDark: $paperDark;
  }
```

