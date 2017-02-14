# Creating a service 

`app.use` has two parameters, a callback function and service name.

Adding a simple service
```js
app.use(function(serviceName) {
  return  'Himanshu';
}, 'myName');
```

The callback function will be called by Reazy with the argument serviceName(`myName`) and the returned data is added to services in the app instance.

Access this service
```js
console.log(app.get('myName'));
// Himanshu
```

To make `src/app.js` less cluttered, lets move the service function to a new file `index.js` inside `src/services/my-name`. The contents of this file will look like this
```js
export default function() {
  return  'Himanshu';
}
```

In `src/app.js`, intialize this service
```js
import myName from 'src/services/my-name';

app.use(myName, 'myName');
```

Your service might be dependent on another service or other data that you want to pass down to the service during intialization. To do this, you need to wrap your service function inside a parent function.
`src/services/my-name/index.js`
```js
export default function(http) {
  return function(serviceName) {
    const name = http.request('get/my/name');
    return name;
  }
}
```
`src/app.js`
```js
import http from 'reazy-http';
import myName from 'src/services/my-name';

app.use(myName(http), 'myName');
```

Reazy calls the service function with `this` reference set to app instance. Therefore, you can get the app instance in your service
```js
export default function(http) {
  return function(serviceName) {
    const app = this;
    const name = http.request('get/my/name');
    app[serviceName] = name;

    return name;
  }
}
```

Now you can access `myName` service in two ways
```js
const name = app.get('myName');
```
or
```js
const name = app.myName;
```

**Note:** To prevent name collision of services, `serviceName` is provided as a parameter to the service function. Whenever your service is modifying app instance, it is recommended that you do add a serviceName property to `app` and do all the modifications inside that.
