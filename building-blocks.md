# Building blocks

To understand the building blocks better, let's look at the generated folder structure first

### Folder structure

```
├── .env
├── .env.example
├── package.json
├── android
├── ios
├── index.android.js
├── index.ios.js
└── src
    ├── app.js
    ├── components
    │   ├── Home
    │   │   └── index.js
    │   └── Routes.js
    ├── models
    ├── services
    │   ├── react-native
    └── stores
        ├── domain
        └── view
```

### Entry point

`app.js` is the entry point of your app. Your Reazy app instance is created and all the services are initialized here.

### Components

The React Native app components will reside inside `src/components`.

### Services

`src/services` contains all the custom services of your app. By default, react-native will be there as a service.
You can create a service for your app inside this folder. 

Know more about services [here](services/readme.md).

### Stores

For state management in a Reazy app, [MobX](https://mobx.js.org/) is included by default.

- `src/stores/domain` contains the domain stores. The data for entities in your app(e.g User, Order, Merchant) will be part of domain stores.

- `src/stores/view` contains the view stores. The data related to the View layer(like loading status, form fields' value, etc.) will be part of view stores.

Know more about stores [here](stores/readme.md).

### Models

`src/models` will conatin models for MobX stores

### Config

`.env` file will be used for storing the config variables. Your app will have a plugin included by default; [reazy-native-config](https://www.npmjs.com/package/reazy-native-config), which helps you set and get the configuration for your app.
