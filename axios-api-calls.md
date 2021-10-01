---
description: Mock API calls and setup Saga middle-tier
---

# Axios & Saga for API

## Mock Calls

DashboardKit uses fack/mock data to render some pages and actions. Mocking has been achieved with help of Axios. It helps users to do minimal changes to load live data. Users just need to change the mock API URL to the Live service URL.

### Setup axios

Axios has been added request interceptor in the file **`..src\utils\axios.js`** so that every request intercept through this.

{% code title="src\\utils\\axios.ts" %}
```javascript
/**
 * axios setup to use mock service
 */

import axios from 'axios';

const axiosServices = axios.create();

// interceptor for http
axiosServices.interceptors.response.use(
    (response) => response,
    (error) => Promise.reject((error.response && error.response.data) || 'Wrong Services')
);

export default axiosServices;

```
{% endcode %}

#### Setup axios-mock-adapter

{% code title="src\\utils\\mockAdapter.ts" %}
```javascript
/**
 * Adaptor for axios
 */

import AxiosMockAdapter from 'axios-mock-adapter';
import axios from './axios';
//  import axios from 'axios';

const services = new AxiosMockAdapter(axios, { delayResponse: 0 });
export default services;

```
{% endcode %}

### How data get loaded in to component?

To understand this, we are going to take example of one app panel and try to understand it. Lets say i want to load data for [leave page of SIS panel](http://dashboardkit.io/react/sis/sis-leave).  There are following things need to be done.

1. Create reducer action
2. Create reducer to update store
3. Setup saga and worker to listen every request
4. Create Axios servive to be called from Saga worker
5. Finally dispatch action from compoent to get data

* Create reducer action

{% code title="src\\store\\actions.ts" %}
```javascript
...
// SIS ACTIONS START
export const FETCH_LEAVE_LIST = 'FETCH_LEAVE_LIST';
export const fetchLeaveList = (): ReducerAction => ({
    type: FETCH_LEAVE_LIST
});

export const FETCH_LEAVE_LIST_SUCCESS = 'FETCH_LEAVE_LIST_SUCCESS';
export const FETCH_LEAVE_LIST_ERROR = 'FETCH_LEAVE_LIST_ERROR';
...
```
{% endcode %}

* Create reducer to update store after getting response back from saga

{% code title="src\\store\\reducers\\sis.ts" %}
```javascript
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
```
{% endcode %}

*  The component dispatches a plain object action to the store. We'll create a Saga that watches for all `FETCH_LEAVE_LIST` actions and triggers an axios API call to fetch the user data. Once response received, we will dispatch another action using 'put' that will update store

{% code title="src\\store\\sagas\\sis.ts" %}
```javascript
...
...
function* workerFetchLeaveList(action: ReducerAction) {
    try {
        const response: AxiosResponse<Array<Result>> = yield call(getLeaves); // Axios call

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
...
...

function* watcherFetchLeaveList() {
    yield takeEvery(FETCH_LEAVE_LIST, workerFetchLeaveList);
}

```
{% endcode %}

* We done setup saga, now we will define axios service, so that it returns data.

{% code title="src\\services\\sis.ts" %}
```javascript
import axios from 'utils/axios';

export const getLeaves = () => axios.get('/api/sis/leaves');

...

```
{% endcode %}

* Axios call will happen and returns data.

{% code title="src\\\_mockApis\\sis.ts" %}
```javascript
// project imports
import services from 'utils/mockAdapter';
import { makeData } from 'data/sisData';

// ==============================|| MOCK SERVICES ||============================== //

// Sis API's
services.onGet('/api/sis/leaves').reply(200, makeData(100));
...

```
{% endcode %}

* Now everything has been setup, you can dispatch action to get data from component.

{% code title="src\\views\\panels\\sis\\Leave.tsx" %}
```javascript
...
useEffect(() => {
        if (_.isEmpty(leaveList)) {
            dispatch(fetchLeaveList());
        }
}, [dispatch]);
...
```
{% endcode %}

To know more about redux-saga and axios, refer below:

{% embed url="https://redux-saga.js.org/" %}

{% embed url="https://axios-http.com/" %}



