# Getting started

Install Reazy CLI
```sh
$ npm install -g reazy-cli
```

Generate the app
```sh
$ reazy init MyAwesomeApp [type]
```

**\[type\]:** mobile/web/plugin. Optional (You will be prompted later if you don't specify it here)

  - **mobile:** A simple React Native app with only the basic services.
  
  - **web:** A React project for web. Coming soon!
  
  - **plugin:** Scaffolding for a Reazy plugin.

Run the app
```sh
$ cd MyAwesomeApp
$ react-native run-ios OR react-native run-android
```

To add more awesomeness to your app, [click here](adding-services.md)