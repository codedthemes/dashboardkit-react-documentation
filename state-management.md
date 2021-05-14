---
description: 'Managing context, state and hooks'
---

# State Management

## Context API

Context provides a way to pass data through the component tree without having to pass props down manually at every level.

We are using context for login methods - **`Auth0, JWT, Firebase.`**

## Redux

React Redux is the official React binding for Redux. It lets your React components read data from a Redux store, and dispatch actions to the store to update data.

Redux is a predictable state container for JavaScript apps.

It helps you write applications that behave consistently, run in different environments \(client, server, and native\), and are easy to test.

On top of that, it provides a great developer experience.

## State

With Redux, our application state is always kept in plain JavaScript objects and arrays which means you may not put other things into the Redux state - no class instances, built-in JS types like Map / Set Promise / Date, functions, or anything else that is not plain JS data

The root Redux state value is almost always a plain JS object, with other data nested inside of it.

Based on this information, we should now be able to describe the kinds of values we need to have inside our Redux state:

```javascript
export const initialState = {
    isOpen: 'dashboard', //for active default menu
    navType: config.theme,
    locale: config.i18n,
    rtlLayout: false, // rtlLayout: config.rtlLayout,
    opened: true
};
```

## Designing Actions

Actions are plain JavaScript objects that have a type field. As mentioned earlier, you can think of an action as an event that describes something that happened in the application.

In the same way that we designed the state structure based on the app's requirements, we should also be able to come up with a list of some of the actions that describe what's happening:

* Add a new todo entry based on the text the user entered
* Toggle the completed status of a todo
* Select a color category for a todo
* Delete a todo
* Mark all todos as completed
* Clear all completed todos
* Choose a different "completed" filter value
* Add a new color filter
* Remove a color filter

Based on that list of things that can happen, we can create a list of actions that our application will use:

```javascript
export const LOGIN = 'LOGIN';
export const LOGOUT = 'LOGOUT';
export const MENU_OPEN = '@customization/MENU_OPEN';
export const MENU_TYPE = '@customization/MENU_TYPE';
export const THEME_LOCALE = '@customization/THEME_LOCALE';
export const THEME_RTL = '@customization/THEME_RTL';
export const SNACKBAR_OPEN = '@snackbar/SNACKBAR_OPEN';
export const ACCOUNT_INITIALISE = 'ACCOUNT_INITIALISE';
export const FIREBASE_STATE_CHANGED = 'FIREBASE_STATE_CHANGED';
export const SET_MENU = 'SET_MENU';
```

## **Writing Reducers**

Reducers are functions that take the current state and an action as arguments ****and return a new state result.

```javascript
(state, action) => newState
```

Creating the Root Reducer - A Redux app really only has one reducer function: the "root reducer" function

```javascript
import * as actionTypes from './actions';
import config from '../config';

export const initialState = {
    isOpen: 'dashboard', //for active default menu
    navType: config.theme,
    locale: config.i18n,
    rtlLayout: false, // rtlLayout: config.rtlLayout,
    opened: true
};

const customizationReducer = (state = initialState, action) => {
    switch (action.type) {
        case actionTypes.MENU_OPEN:
            return {
                ...state,
                isOpen: action.isOpen
            };
        case actionTypes.MENU_TYPE:
            return {
                ...state,
                navType: action.navType
            };
        case actionTypes.THEME_LOCALE:
            return {
                ...state,
                locale: action.locale
            };
        case actionTypes.THEME_RTL:
            return {
                ...state,
                rtlLayout: action.rtlLayout
            };
        case actionTypes.SET_MENU:
            return {
                ...state,
                opened: action.opened
            };
        default:
            return state;
    }
};

export default customizationReducer;
```

