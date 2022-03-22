# Creating Custom Widgets | Netlify CMS | Open-Source Content Management System

[https://www.netlifycms.org/docs/custom-widgets/#advanced-field-validation](https://www.netlifycms.org/docs/custom-widgets/#advanced-field-validation)

**Result:**

All widget fields, including those for built-in widgets, [include basic validation](https://www.netlifycms.org/docs/widgets/#common-widget-options) capability using the `required` and `pattern` options.

With custom widgets, the widget control can also optionally implement an `isValid` method to perform custom validations, in addition to presence and pattern. The `isValid` method will be automatically called, and it can return either a boolean value, an object with an error message or a promise. Examples:

**Boolean** No errors:

```
  isValid = () => {
    // Do internal validation
    return true;
  };
```

Existing error:

```
  isValid = () => {
    // Do internal validation
    return false;
  };
```

**Object with `error` (useful for returning custom error messages)** Existing error:

```
  isValid = () => {
    // Do internal validation
    return { error: { message: 'Your error message.' } };
  };
```

**Promise** You can also return a promise from `isValid`. While the promise is pending, the widget will be marked as "in error". When the promise resolves, the error is automatically cleared.

```
  isValid = () => {
    return this.existingPromise;
  };
```

**Note:** Do not create a promise inside `isValid` - `isValid` is called right before trying to persist. This means that even if a previous promise was already resolved, when the user hits 'save', `isValid` will be called again. If it returns a new promise, it will be immediately marked as "in error" until the new promise resolves.

Widgets are inputs for the Netlify CMS editor interface. It's a React component that receives user input and outputs a serialized value. Those are the only rules - the component can be extremely simple, like text input, or extremely complicated, like a full-blown markdown editor. They can make calls to external services, and generally do anything that JavaScript can do.

For writing custom widgets as a separate package you should follow these steps:

1. 
    
    For setting up a new npm package run this command:
    
2. 
    
    Answer the questions in the command line questionnaire.
    
3. 
    
    In order to build React components, we need to set up a build step. We'll be using Webpack. Please run the following commands to install the required dependencies:
    

```
   npm install --save-dev babel-loader@7 babel-core babel-plugin-transform-class-properties babel-plugin-transform-export-extensions babel-plugin-transform-object-rest-spread babel-preset-env babel-preset-react cross-env css-loader html-webpack-plugin netlify-cms react source-map-loader style-loader webpack webpack-cli webpack-serve
```

```
   npm install --save prop-types
```

And you should manually add "**peerDependencies**" and "**scripts**" as shown below.

Here is the content of `package.json` that you will have at the end:

```
{
  "name": "netlify-cms-widget-starter",
  "description": "A boilerplate for creating Netlify CMS widgets.",
  "author": "name of developer",
  "keywords": [
    "netlify",
    "netlify-cms",
    "cms",
    "widget",
    "starter",
    "boilerplate"
  ],
  "version": "0.0.1",
  "homepage": "https://github.com/netlify/netlify-cms-widget-starter",
  "license": "MIT",
  "main": "dist/main.js",
  "devDependencies": {
    "babel-loader": "^7.1.4",
    "babel-plugin-transform-class-properties": "^6.24.1",
    "babel-plugin-transform-export-extensions": "^6.22.0",
    "babel-plugin-transform-object-rest-spread": "^6.26.0",
    "babel-preset-env": "^1.6.1",
    "babel-preset-react": "^6.24.1",
    "cross-env": "^5.1.4",
    "css-loader": "^0.28.11",
    "html-webpack-plugin": "^3.2.0",
    "netlify-cms": "^1.5.0",
    "react": "^16.3.2",
    "source-map-loader": "^0.2.3",
    "style-loader": "^0.20.3",
    "webpack": "^4.6.0",
    "webpack-cli": "^2.0.14",
    "webpack-serve": "^0.3.1"
  },
  "dependencies": {
    "prop-types": "^15.6.1"
  },
  "peerDependencies": {
    "react": "^16"
  },
  "scripts": {
    "start": "webpack-serve --static public --open"
  }
}
```

1.   
    
    Create a Webpack configuration file with this content:
    
    `webpack.config.js`
    
    ```
    const path = require('path')
    const HtmlWebpackPlugin = require('html-webpack-plugin')
    
    const developmentConfig = {
      mode: 'development',
      entry: './dev/index.js',
      output: {
        path: path.resolve(__dirname, 'public'),
      },
      optimization: { minimize: false },
      module: {
        rules: [
          {
            test: /\.js$/,
            loader: 'source-map-loader',
            enforce: 'pre',
          },
          {
            test: /\.jsx?$/,
            exclude: /node_modules/,
            loader: 'babel-loader',
          },
          {
            test: /\.css$/,
            use: [{ loader: 'style-loader' }, { loader: 'css-loader' }],
          },
        ],
      },
      plugins: [
        new HtmlWebpackPlugin(),
      ],
      devtool: 'eval-source-map',
    }
    
    const productionConfig = {
      mode: 'production',
      module: {
        rules: [
          {
            test: /\.jsx?$/,
            loader: 'babel-loader',
          },
        ],
      },
      devtool: 'source-map',
    }
    
    module.exports = process.env.NODE_ENV === 'production' ? productionConfig : developmentConfig
    ```
    
2. 
    
    The `.babelrc` file is our local configuration for our code in the project. You should create it under the root of the application repo. It will affect all files that Babel processes. So, create a `.babelrc` file under the main project with this content:
    

```
{
  "presets": [
    "react",
    "env",
  ],
  "plugins": [
    "transform-export-extensions",
    "transform-class-properties",
    "transform-object-rest-spread",
  ],
}
```

1. Create a `src` directory with the files `Control.js`, `Preview.js` and `index.js`

`src/Control.js`

```
 import PropTypes from 'prop-types';
 import React from 'react';

 export default class Control extends React.Component {
   static propTypes = {
     onChange: PropTypes.func.isRequired,
     forID: PropTypes.string,
     value: PropTypes.node,
     classNameWrapper: PropTypes.string.isRequired,
   }

   static defaultProps = {
     value: '',
   }

   render() {
     const {
       forID,
       value,
       onChange,
       classNameWrapper,
     } = this.props;

     return (
       <input
         type="text"
         id={forID}
         className={classNameWrapper}
         value={value || ''}
         onChange={e => onChange(e.target.value)}
       />
     );
   }
 }
```

`src/Preview.js`

```
import PropTypes from 'prop-types';
import React from 'react';

export default function Preview({ value }) {
  return <div>{ value }</div>;
}

Preview.propTypes = {
  value: PropTypes.node,
};
```

`src/index.js`

```
import Control from './Control'
import Preview from './Preview'

if (typeof window !== 'undefined') {
  window.Control = Control
  window.Preview = Preview
}

export { Control, Preview }
```

1. Now you need to set up the locale example site. Under the main project, create a `dev` directory with the files `bootstrap.js` and `index.js`

`bootstrap.js`

```
window.CMS_MANUAL_INIT = true
```

`index.js`

```
import './bootstrap.js'
import CMS, { init } from 'netlify-cms'
import 'netlify-cms/dist/cms.css'
import { Control, Preview } from '../src'

const config = {
backend: {
 name: 'test-repo',
 login: false,
},
media_folder: 'assets',
collections: [{
 name: 'test',
 label: 'Test',
 files: [{
   file: 'test.yml',
   name: 'test',
   label: 'Test',
   fields: [
     { name: 'test_widget', label: 'Test Widget', widget: 'test'},
   ],
 }],
}],
}

CMS.registerWidget('test', Control, Preview)

init({ config })
```

To run a copy of Netlify CMS with your widget for development, use the start script:

Your widget source is in the `src` directory, where there are separate files for the `Control` and `Preview` components.

You'll want to take a few steps before publishing a production built package to npm:

1.  
    
    Customize `package.json` with details for your specific widget, e.g. name, description, author, version, etc.
    
    ```
    {
      "name": "netlify-cms-widget-starter",
      "description": "A boilerplate for creating Netlify CMS widgets.",
      "author": "name of developer",
      "keywords": [
        "netlify",
        "netlify-cms",
        "cms",
        "widget",
        "starter",
        "boilerplate"
      ],
      "version": "0.0.1",
      // ... rest
    }
    ```
    
2. 
    
    For discoverability, ensure that your package name follows the pattern `netlify-cms-widget-<name>`.
    
3. 
    
    Delete this `README.md`, rename `README_TEMPLATE.md` to `README.md`, and update the new file for your specific widget.
    
4. 
    
    Rename the exports in `src/index.js`. For example, if your widget is `netlify-cms-widget-awesome`, you would do:
    

```
if (typeof window !== 'undefined') {
  window.AwesomeControl = Control
  window.AwesomePreview = Preview
}

export { Control as AwesomeControl, Preview as AwesomePreview }
```

1. Optional: customize the component and file names in `src`.
2. If you haven't already, push your repo to your GitHub account so the source available to other developers.
3. Create a production build, which will be output to `dist`:

```
npm run build
```

1. Finally, if you're sure things are tested and working, publish!

```
npm publish
```