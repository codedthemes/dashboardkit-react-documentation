---
description: 'A File Structure allows applications to read, write and modify data.'
---

# File Structure

File Structures is the Organization of Data in Secondary Storage Device in such a way that minimizes the access time and the storage space. A File Structure is a combination of representations for data in files and of operations for accessing the data.

## Project structure

Under the `able-pro-material/`the folder you will find the project folder structure.

```text
able-pro-material/
├── package.json             -> Package json file.
├── public/
│   ├── favicon.ico
│   ├── index.html
└── src/
    ├── assets/
    |    ├── images/
    |    ├── scss/           -> Template SCSS files, check folder structure below  
    ├── components/          -> Template custom components
    ├── contexts/        
    ├── firebase/            -> Firebase login lib
    ├── hooks/               -> Custom hooks
    ├── layout/
    |    ├── MainLayout      -> Layout components & routers
    |    ├── MinimalLayout   -> Minimal Layout components
    |    ├── App.js
    ├── services/            -> Data services 
    ├── store/               -> Redux actions, reducers & types
    ├── themes/              -> Material default theme
    ├── views/               -> View files for all pages
    ├── config.js            -> Template constant value and live customization  
    ├── index.js             -> Application root js file
    ├── menu-item.js         -> Allication menu data
    ├── Routes.js            -> Add pages router
```

## JSS with SCSS Structure

Under the `able-pro-material/src/assets/scss/`the folder you will find the following folder structure.

```text
SCSS/
├── custom/          -> 
├── plugins/              -> Third party plugins customisation scss
├── _themes-vars.scss     -> theme veriables
├── style.scss             -> Application main file
```

