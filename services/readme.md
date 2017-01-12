# Services 

As reazy is a service-based framework, almost everything in your app is a service.

You can initialize your service using `app.use`
```js
app.use(service(), 'serviceName');
```

The service will be registered with the name `serviceName` and can be accessed like this:
```js
const myService = app.get('serviceName');
myService.someFunction();
```


Every service has access to the Reazy app instance. Some services can add their own objects or functions to the app instance. For example, [reazy-native-config](https://www.npmjs.com/package/reazy-native-config) service adds config object to the app. So you have two ways to access the config service:
```js
const config = app.get('config');
```
or
```js
const config = app.config
```

Let's [get started](create-service.md) on how you can create your own services.