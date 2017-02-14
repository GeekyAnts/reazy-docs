# Adding services


### Manual

Let's add a new service `reazy-auth` which is available as a reazy plugin.
```sh 
$ npm install --save reazy-auth
```

Open `src/app.js`.
```js
import reazy from 'reazy';
import auth from 'reazy-auth';                    // <-- import the service
import reactNative from './services/react-native';

const app = reazy();

app.use(auth(), 'auth');                          // <-- Initialize the service
app.use(reactNative(), 'reactNative');

export default app;
```

### Using CLI

Some services which are available as npm packages can be added using [reazy-cli](https://www.npmjs.com/package/reazy-cli).

```sh
$ reazy add auth
```

This command will install `reazy-auth` npm package and also add the above mentioned lines in your `app.js`.

If this package doesn't contain the script to edit your files, the CLI will let you know. This means you will have to import and initialize the service yourself.

[Learn more and create your own services](services/readme.md)

Now that we are done with the basic usage, let's dive into the details.