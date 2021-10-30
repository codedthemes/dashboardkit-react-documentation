---
description: Configuration option for entire DashboardKit Template
---

# Project Configuration

DashboardKit has a single source of truth for default configuration which lets users manage it effectively. It also makes it scalable for new configurations. you can set config like font, border, theme layout, locale, etc. All those can be configured at `src\config\constant.ts`

| **Option**      | **Default**      | **Data Type** | **Description**                                                 |
| --------------- | ---------------- | ------------- | --------------------------------------------------------------- |
| BASENAME        | /                | String        | `build time set subdomain or path of project directory`         |
| BASE\_URL       | /dashboard/sales | string        | default path                                                    |
| BASE\_TITLE     | -                | String        | set page title                                                  |
| layout          | vertical         | number        | layout option. i.e.                                             |
| layoutType      | dark-sidebar     | String        | layout options. i.e. light-sidebar, dark-sidebar                |
| pageType        | -                | String        | app-dark-mode                                                   |
| colorBrand      | -                | boolean       | bg-primary, bg-danger, bg-warning, bg-info, bg-success, bg-dark |
| headerBackColor | -                | Object        | bg-primary, bg-danger, bg-warning, bg-info, bg-success, bg-dark |

{% tabs %}
{% tab title="config.js" %}
{% code title="src\config\constant.ts" %}
```javascript
// imports from project
export const BASENAME = '/react';
export const BASE_URL = '/dashboard/sales';
export const BASE_TITLE = ' | DashboardKit React Bootstrap 5 Admin Template';

// -----------------------|| Application default Configuration ||-----------------------//
export const CONFIG = {
    layout: 'vertical', // vertical, horizontal
    layoutType: 'dark-sidebar', // light-sidebar
    pageType: '', // app-dark-mode
    colorBrand: 'bg-danger', // bg-primary, bg-danger, bg-warning, bg-info, bg-success, bg-dark
    headerBackColor: 'bg-danger' // bg-primary, bg-danger, bg-warning, bg-info, bg-success, bg-dark
};

```
{% endcode %}
{% endtab %}
{% endtabs %}
