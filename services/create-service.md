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

Your service might need some configuration before initialization. To do this, you need to wrap your service function inside a [higher-order function](https://www.sitepoint.com/higher-order-functions-javascript/#returning-functions-as-results) and call that higher-order function in your `app.use`.

`src/services/my-name/index.js`
```js
export default function(config) {
  return function(serviceName) {
    return `${name} ${config.lastName}`;
  }
}
```
`src/app.js`
```js
import http from 'reazy-http';
import myName from 'src/services/my-name';

app.use(myName({lastName: 'Satija'}), 'myName');
```

Reazy calls the service function with `this` reference set to app instance. Therefore, you can get the app instance in your service
```js
export default function(http) {
  return function(serviceName) {
    const app = this;

    app[serviceName] = `${name} ${config.lastName}`;

    return `${name} ${config.lastName}`;
  }
}
```

Now you can access `myName` service in two ways
```js
const name = app.get('myName');
// Himanshu Satija
```
or
```js
const name = app.myName;
// Himanshu Satija
```

**Note:** To prevent name collision of services, `serviceName` is provided as a parameter to the service function. Whenever your service is modifying app instance, it is recommended that you do add a serviceName property to `app` and do all the modifications inside that.
