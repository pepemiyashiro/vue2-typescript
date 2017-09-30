# vue2-typescript

> A Vue.js project

> The build has been generated by the vue-cli.
> This is a guide about how to implement TypeScript.

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report

# run unit tests
npm run unit

# run e2e tests
npm run e2e

# run all tests
npm test
```

For detailed explanation on how things work, checkout the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).

# Using TypeScript

## Install dependencies
```bash
npm i -D typescript ts-loader vue-class-component
```

## Add TypeScript recommended configuration
tsconfig.json

```json
{
  "compilerOptions": {
    "lib": [
      "dom",
      "es5",
      "es2015.promise"
    ],
    "module": "es2015",
    "moduleResolution": "node",
    "target": "es5",
    "sourceMap": true,
    "emitDecoratorMetadata": true,
    "experimentalDecorators": true,
    "allowSyntheticDefaultImports": true
  }
}
```

## Add the file vue-shim.d.ts in the root folder

```typescript
declare module "*.vue" {
  import Vue from 'vue'
  export default Vue
}

```


## Update the Webpack Base config file

```javascript

entry: {
  app: './src/main.ts'
},
...

...
resolve: {
    extensions: ['.ts', '.js', '.vue', '.json'],
}
...

...
module: {
    rules: [
      {
        test: /\.ts$/,
        exclude: /node_modules|vue\/src/,
        loader: 'ts-loader',
        options: {
          appendTsSuffixTo: [/\.vue$/]
        }
      },
...

```

## Component Declaration

Inside a .vue file

```typescript
<script lang="ts"> // Declare lang

  import Vue from 'vue'
  import Component from 'vue-class-component'

  @Component({}) // use decorators
  export default class Hello extends Vue {
    name: string = 'hello'; // declare types

    get fullMessage() {
      return `Welcome to Vue 2 with Typescript`;
    }
  }
  
</script>
```

# Styles

For styles you don't need to do any configuration. But you need to declare which CSS pre-processor you are using.
(I have waste some time to trying to make my own configuration, but Vue-cli have everything you need... )

## Declaration
```CSS
  <style lang="scss"> /* avaliable: css, postcss, less, sass, scss, stylus or styl */
  .box {
    background-color: red;  
    &__title {
      color: #dedede;
    }
  }
  </style>
```

## Imports
```CSS
  <style lang="scss"> /* avaliable: css, postcss, less, sass, scss, stylus or styl */
  @import '../assets/scss/global/global'; /* my change depending on the lang */
  .box {
    background-color: red;  
    &__title {
      color: #dedede;
    }
  }

</style>
```

## Scoped CSS Rules
Adding the attribute scoped, Vue will generate a data attributes to encapsulate the CSS rules.
They will be unique, and scoped to the component, where the style is been used.
```CSS
  <style lang="scss" scoped> /* avaliable: css, postcss, less, sass, scss, stylus or styl */
  .box {
    background-color: red;  
    &__title {
      color: #dedede;
    }
  }
  </style>
```

# References:
- [Vue Documentation](https://vuejs.org/)
- [Vue + TypeScript - egghead.io](https://egghead.io/courses/use-typescript-to-develop-vue-js-web-applications)
