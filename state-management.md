---
description: Managing context, state and hooks
---

# State Management

## Context API

Context provides a way to pass data through the component tree without having to pass props down manually at every level.

## Redux

React Redux is the official React binding for Redux. It lets your React components read data from a Redux store, and dispatch actions to the store to update data.

Redux is a predictable state container for JavaScript apps.

It helps you write applications that behave consistently, run in different environments (client, server, and native), and are easy to test.

On top of that, it provides a great developer experience.

## Redux-Saga

Redux-saga library aims to make application side effects (i.e. asynchronous things like data fetching and impure things like accessing the browser cache) easier to manage, more efficient to execute, easy to test, and better at handling failures. Sagas enable numerous approaches to tackling parallel execution, task concurrency, task racing, task cancellation, and more. Keep total control over the flow of your code.

Dashboard-Kit uses redux-saga as middleware to manage many things. There are 6 sagas in application for each app in theme. Given example below is saga for SIS app of dashboard-kit.

{% tabs %}
{% tab title="JavaScript" %}
```javascript
```
{% endtab %}

{% tab title="TypeScript" %}
```typescript
// third party
import { takeEvery, fork, put, call } from 'redux-saga/effects';
import { AxiosResponse } from 'axios';

// project imports
import {
    FETCH_LEAVE_LIST,
    ...
} from 'store/actions';
import { ReducerAction } from 'types/application';
import { Result } from 'types/table';
import { getLeaves, getEvaluations } from 'services/sis';

function* workerFetchLeaveList(action: ReducerAction) {
    try {
        const response: AxiosResponse<Array<Result>> = yield call(getLeaves);

        yield put({
            type: FETCH_LEAVE_LIST_SUCCESS,
            payload: response.data || []
        });
    } catch (error) {
        yield put({
            type: FETCH_LEAVE_LIST_ERROR,
            error
        });
    }
}


function* watcherFetchLeaveList() {
    yield takeEvery(FETCH_LEAVE_LIST, workerFetchLeaveList);
}


export default [fork(watcherFetchLeaveList)];

```
{% endtab %}
{% endtabs %}

## State

With Redux, our application state is always kept in plain JavaScript objects and arrays which means you may not put other things into the Redux state - no class instances, built-in JS types like Map / Set Promise / Date, functions, or anything else that is not plain JS data

The root Redux state value is almost always a plain JS object, with other data nested inside of it.

Based on this information, we should now be able to describe the kinds of values we need to have inside our Redux state.

As we are using redux-saga, the state gets an auto-update from saga once the reponse is received.

{% tabs %}
{% tab title="JavaScript" %}
```javascript
export const initialState = {
    isOpen: 'dashboard', //for active default menu
    navType: config.theme,
    locale: config.i18n,
    rtlLayout: false, // rtlLayout: config.rtlLayout,
    opened: true
};
```
{% endtab %}

{% tab title="TypeScript" %}
```typescript
export const initialState = {
    isOpen: 'dashboard', //for active default menu
    navType: config.theme,
    locale: config.i18n,
    rtlLayout: false, // rtlLayout: config.rtlLayout,
    opened: true
};
```
{% endtab %}
{% endtabs %}

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

{% tabs %}
{% tab title="JavaScript" %}
```javascript
```
{% endtab %}

{% tab title="Typescript" %}
```typescript
...
// SIS ACTIONS START
export const FETCH_LEAVE_LIST = 'FETCH_LEAVE_LIST';
export const fetchLeaveList = (): ReducerAction => ({
    type: FETCH_LEAVE_LIST
});
...
```
{% endtab %}
{% endtabs %}

## **Writing Reducers**

Reducers are functions that take the current state and an action as arguments and return a new state result.

```javascript
(state, action) => newState
```

Creating the Root Reducer - A Redux app really only has one reducer function: the "root reducer" function

{% tabs %}
{% tab title="JavaScript" %}
```javascript
```
{% endtab %}

{% tab title="Typescript" %}
```typescript
// third party
import { Reducer, combineReducers } from 'redux';
import _ from 'lodash';

// project imports
import * as actionTypes from 'store/actions';
import { ReducerAction, ReducerInitialState, InitialState } from 'types/application';

const leaveList: Reducer<ReducerInitialState> = (state = InitialState, action: ReducerAction) => {
    switch (action.type) {
        case actionTypes.FETCH_LEAVE_LIST_SUCCESS: {
            return { data: _.get(action, 'payload', []), error: {} };
        }

        case actionTypes.FETCH_LEAVE_LIST_ERROR: {
            return { data: {}, error: _.get(action, 'error', {}) };
        }

        default:
            return state;
    }
};


export default {
    sis: combineReducers({
        leaveList,
    })
};

```
{% endtab %}
{% endtabs %}

## How to Remove redux-saga?

redux-saga is very helpful to manage API calls in big-scale applications. If you still don't want to use saga, you can remove it from the middle tier.&#x20;

**todo: add steps to remove saga**
