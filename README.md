# eslint-config

Sprii [eslint](http://eslint.org/) configurations. Based off https://github.com/moxystudio/eslint-config.


## Installation

`$ npm install --save-dev eslint @sprii/eslint-config`

Additional dependencies that need to be installed per addon:

react addon: `$ npm install --save-dev eslint-plugin-react@^3.13.0`

This config was tested with `eslint@^4.3.0` and the specific version ranges for plugins. Use other versions at your own risk. I will try to keep this project up to date with the changes of `eslint` and the plugins used here.


## Usage

First you need to choose the **base** configuration to use:

- `es5` - The configuration to be used in ECMAScript 5 based projects
- `es6` - The configuration to be used in ECMAScript 6 based projects

Then enhance it with one or more **addons**:

- `browser` - If you are going to develop code for the browser (having in mind IE >= 9)
- `node` - If you are going to develop code for NodeJS
- `node-v4-es6` - If you are going to develop code for NodeJS >= 4 with the `es6` base configuration
- `es6-modules` - If you are going to use ES6 import & export (must be used with the `es6` base configuration)
- `react` - If you are going to use React and JSX (requires `eslint-plugin-react`)

Finally, simply create a `.eslintrc.json` file with the chosen base configuration and addons. Feel free to override rules you won't agree with. You can look at some examples bellow.

Alternatively, you can make your own configuration by using the set of **rules** individually. If you're interested in doing that, you can check `es5.js` to see how it is done.


### Examples

Cutting edge ES6 with modules in the browser, using react:

```json
{
    "root": true,
    "extends": [
        "@carsy/eslint-config/es6",
        "@carsy/eslint-config/addons/es6-modules",
        "@carsy/eslint-config/addons/browser",
        "@carsy/eslint-config/addons/react"
    ]
}
```

Cutting edge ES6 with modules in NodeJS (requires babel or similar):

```json
{
    "root": true,
    "extends": [
        "@carsy/eslint-config/es6",
        "@carsy/eslint-config/addons/es6-modules",
        "@carsy/eslint-config/addons/node"
    ]
}
```

Use ES6 in NodeJS without any transpiler:

```json
{
    "root": true,
    "extends": [
        "@carsy/eslint-config/es6",
        "@carsy/eslint-config/addons/node"
    ]
}
```

.. and if you are programming against NodeJS v4 please use:

```json
{
    "root": true,
    "extends": [
        "@carsy/eslint-config/es6",
        "@carsy/eslint-config/addons/node"
        "@carsy/eslint-config/addons/node-v4-es6"
    ]
}
```


Good old ES5 in NodeJS:

```json
{
    "root": true,
    "extends": [
        "@carsy/eslint-config/es5",
        "@carsy/eslint-config/addons/node"
    ]
}
```

Note that by setting `root` to true, we ensure that no ancestor configuration is used which also improves `eslint` performance because no more file lookups need to be done.


## File name convention

If your file exports a single class, your filename should be exactly the name of the class. For other cases, the name of the file should be the same as the default exports (prefer camelCase).


## License

[MIT License](http://opensource.org/licenses/MIT)
