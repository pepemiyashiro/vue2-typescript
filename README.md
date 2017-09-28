# sassy-vue2

> A Vue.js project

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

Insider a *.vue files

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



