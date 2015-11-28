# Redux Universal Starter

#### Why?

This starter forked off of [react-redux-universal-hot-example](https://github.com/erikras/react-redux-universal-hot-example) with the goal of making an npm module for an easier starting point for new projects. Please refer to the README there for more details and join the discussion at the pull request here: https://github.com/erikras/react-redux-universal-hot-example/pull/626, and please open an issue if you find one.

#### Usage

An example project has been made here: https://github.com/bdefore/react-redux-universal-hot-example/tree/example-project and is deployed on Heroku here: https://redux-universal-starter.herokuapp.com

- Install

```
npm install redux-universal-starter
```

- Add a `webpack` object in `src/config.js` that defines what properties you want to override during the build step.

```
  const path = require('path');
  const sourceRoot = path.resolve(__dirname);
  const projectRoot = path.resolve(__dirname, '..');

  ...

  webpack: {
    context: projectRoot,
    entry: {
      main: [
        'bootstrap-sass!' + sourceRoot + '/theme/bootstrap.config.js',
        'font-awesome-webpack!' + sourceRoot + '/theme/font-awesome.config.js'
      ]
    },
    output: {
      path: projectRoot + '/static/dist'
    },
    resolve: {
      root: sourceRoot,
      alias: {
        routes: sourceRoot + '/routes.js',
        config: sourceRoot + '/config.js',
        reducers: sourceRoot + '/redux/modules/reducer.js',
        actions: sourceRoot + '/api/actions/index.js'
      }
    }
  }
```

- Specify your build steps 

The following npm bin aliases have been defined:

```
redux-universal-starter-watch
redux-universal-starter-server
redux-universal-starter-api
redux-universal-starter-build
```

You'll generally call these from the corresponding section of your project's scripts. See `package.json` in the example project: https://github.com/bdefore/react-redux-universal-hot-example/blob/example-project/package.json#L39

#### Local development

If you'd like to modify the starter while running a project that uses it, I've found that npm version 2 tends to cause issues including multiple versions of React, which cause script errors, if you symlink or drop it into your project's `node_modules` manually. You may prefer to use `PROJECT_ROOT=/path/to/project npm run dev` from the starter root, which will watch for changes and copy them over to your project's `node_modules/redux-universal-starter/lib` directory.

#### Known Issues

- In the example project, Bootstrap and Font Awesome styles are not built into the Webpack styles, so do not serverside render.
- An extra resolve exists for `node_modules/redux-universal-test/node_modules`. This may not be a correct assumption.
- Extending the functionality of `src/client` is currently difficult without forking.
