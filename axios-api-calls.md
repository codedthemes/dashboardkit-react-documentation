---
description: Mock API calls
---

# Axios API Calls

## Mock Calls

DashboardKit uses fack/mock data to render some pages and actions. Mocking has been achieved with help of Axios. It helps users to do minimal changes to load live data. Users just need to change the mock API URL to the Live service URL.

### How does it work?

Axios has been configured in the folder **`..src\utils\axios.js`**

To use Axios on a page, you need to import it and make a call. After that, you need to make calls to Axios using **`axios.get('path')`** `or` **`axios.post('path')`** see below implementation.

{% code title="axios.js" %}

```javascript
...
import axios from '../../../../utils/axios'; // 1. import axios
...

const CardListPage = () => {
    const [data, setData] = React.useState([]);

    ...
    ...

    // get dummy data
    const getData = async () => {
        const response = await axios.get('/api/chat/users'); // 2. change it to live service URL
        setData(response.data.users);
        return response.data.users;
    };

    ...
    ...

    // 3. call to get data
    React.useEffect(() => {
        getData();
    }, []);

    ...
    ...

    // use data in HTML
    {Object.keys(data).map((key, index) => {
        return (
            <React.Fragment key={index}>

            ...
            ...

            </React.Fragment>
            );
    ...
    ...

        })
    };

};

export default SamplePage;
```

{% endcode %}

DashboardKit has all dummy data in folder **`src\_mockApis.`** For API, **`api/chat/users`**, following data configured in **`..\src_mockApis\chat\index.js`** :

{% code title="\\chat\\index.js" %}

```javascript
import services from './../../utils/mockAdapter';

...

let users = [
    {
        id: 1,
        name: 'Alene',
        company: 'ABC Pvt Ltd',
        role: 'Sr. Customer Manager',
        work_email: 'alene_work@company.com',
        personal_email: 'alene@company.com',
        work_phone: '380-293-0177',
        personal_phone: '380-293-0177',
        location: 'Port Narciso',
        avatar: 'avatar-1.png',
        status: 'Laboris non ad et',
        lastMessage: '2h ago',
        birthdayText: 'happy Birthday Alene',
        unReadChatCount: 2,
        online_status: 'available'
    },
    {
        id: 2,
        name: 'Keefe',
        company: 'ABC Pvt Ltd',
        role: 'Dynamic Operations Officer',
        work_email: 'keefe_work@gmil.com',
        personal_email: 'keefe@gmil.com',
        work_phone: '253-418-5940',
        personal_phone: '253-418-5940',
        location: 'Afghanistan',
        avatar: 'avatar-2.png',
        status: 'Laboris non ad et',
        lastMessage: '1:20 AM',
        birthdayText: 'happy Birthday Keefe',
        unReadChatCount: 3,
        online_status: 'available'
    }
    ...
    ...
];
...
...
];
services.onGet('/api/chat/users').reply(200, {users: users});
...
...
});

```

{% endcode %}

You can configure the same for `post`methods as well.
