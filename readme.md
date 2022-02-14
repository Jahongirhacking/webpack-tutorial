# Installations
npm init -y  --> create a default package.json

npm i webpack webpack-cli --save-dev  -->  set up webpack

- create `src` folder and add `index.js` file to it

- "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "dev": "webpack --mode development",
    "build": "webpack --mode production"
  }  -->  shortcuts `npm run dev`

npx webpack --mode development  -->  create a dist folder

- then we have to create `webpack.config.js` file inside the root folder and write some codes

npm i webpack-dev-server --save-dev  -->  create a server

- "dev": "webpack serve --mode development",


- install babel for translate
npm i -D @babel/core @babel/preset-env babel-loader

create `.babelrc` file

# Plugins
* npm i html-webpack-plugin --save-dev  -->  html plugin

* Install the plugin via yarn or npm

* Declare a new instance of the plugin in the plugins list

* Require the plugin from the node modules directory


# Modes (Development and production)
* mode: "production",  -->config file

* mode: 'development',
* devtool: 'source-map',

* create `webpack.dev.js` and `webpack.prod.js` files

- change the piece of `package.json` to:
* "build-prod": "webpack --config webpack.prod.js"


# Install Webpack Dev Server**
* npm i webpack-dev-server --save-dev

* "build-dev": "webpack --config webpack.dev.js --watch --info-verbosity verbose"

* "open-dev": "webpack-dev-server --config webpack.dev.js --open"

* npm i -D clean-webpack-plugin

* Add a require statement to the top of the webpack config file:
* const { CleanWebpackPlugin } = require('clean-webpack-plugin');


# SASS
* npm i -D style-loader node-sass css-loader sass-loader

`{
    test: /\.scss$/,
    use: [ 'style-loader', 'css-loader', 'sass-loader' ]
}`

# Development
`entry: './src/client/index.js',
mode: 'development',
devtool: 'source-map',
stats: 'verbose',`

# Production
`create a cloud called `Client`
output:{
  libraryTarget: "var",
  library: "Client"
}`

* exporting client js files to the cloud

`export {
  checkForname,
  handleSubmit
}`

and then all functions will be written like `Client.handleSubmit(event)`


# Minify CSS
* npm i mini-css-extract-plugin --save-dev
* const MiniCssExtractPlugin=require("mini-css-extract-plugin")
* new MiniCssExtractPlugin({filename:"[name].css"})

* npm install --save-dev mini-css-extract-plugin terser-webpack-plugin@4 optimize-css-assets-webpack-plugin

`const MiniCssExtractPlugin = require('mini-css-extract-plugin');
const OptimizeCSSAssetsPlugin = require('optimize-css-assets-webpack-plugin');
const TerserPlugin = require('terser-webpack-plugin');`

`optimization: {
  minimizer: [new TerserPlugin({}), new OptimizeCSSAssetsPlugin({})],
},`


# Service Workers
* npm install workbox-webpack-plugin --save-dev

* const WorkboxPlugin = require('workbox-webpack-plugin');

* new WorkboxPlugin.GenerateSW()

`<script>
// Check that service workers are supported
if ('serviceWorker' in navigator) {
   // Use the window load event to keep the page load performant
   window.addEventListener('load', () => {
        navigator.serviceWorker.register('/service-worker.js');
   });
}
</script>`
