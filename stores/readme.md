# Stores

[MobX](https://mobx.js.org/) is a simple, scalable state management library which is available by default with Reazy app. We recommend to check out their [docs](https://mobx.js.org/) before using this in your Reazy app.

Data stores in your app should reside in `src/stores`. There are two types of stores: Domain stores and View stores.

The data for entities in your app(e.g User, Order, Merchant) will be part of domain stores and the data related to the view layer(like loading status, form fields' value, etc.) will be part of view stores.

MobX service is there inside `src/services/mobx` which has a function called `getAllStores`. This function combines all the stores in your app into a single object. In this object, view stores will be named as `'view.storeName'` while domain stores will be named `'domain.storeName'`.