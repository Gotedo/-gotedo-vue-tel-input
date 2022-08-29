<p align="center">
<img width="100" alt="vue-tel-input-logo" src="https://iamstevendao.github.io/vue-tel-input/hero.png"/>
</p>

# vue-tel-input

International Telephone Input with Vue.

[![npm](https://img.shields.io/npm/dt/@gotedo/vue-tel-input.svg)](https://www.npmjs.com/package/@gotedo/vue-tel-input) [![stars](https://img.shields.io/github/stars/gotedo/vue-tel-input.svg)](https://github.com/gotedo/vue-tel-input)

<p align="center">
<img width="600" alt="In-action GIF" src="https://thumbs.gfycat.com/EducatedPoliteBluefintuna-size_restricted.gif"/>
</p>

## Credits

This repo is an offshoot clone of the [vue-tel-input](https://github.com/iamstevendao/vue-tel-input) project by [Steven Dao](https://github.com/iamstevendao)

## Documentation and Demo

[Readme](https://github.com/gotedo/vue-tel-input)

## Changelog

[Go to Github Releases](https://github.com/gotedo/vue-tel-input/releases)

## Getting started

- Install the plugin:

  ```sh
  npm install @gotedo/vue-tel-input
  ```

- Add the plugin into your app:

  ```javascript
  import Vue from 'vue';
  import VueTelInput from '@gotedo/vue-tel-input';
  import '@gotedo/vue-tel-input/dist/vue-tel-input.css';

  Vue.use(VueTelInput);
  ```

  [More info on installation](#installation)

- Use the `vue-tel-input` component:

  ```html
  <template>
    <vue-tel-input v-model="phone"></vue-tel-input>
  </template>
  ```

## Installation

### npm

```bash
  npm install vue-tel-input
```

Install the plugin into Vue:

```javascript
import Vue from 'vue';
import VueTelInput from '@gotedo/vue-tel-input';
import '@gotedo/vue-tel-input/dist/vue-tel-input.css';

Vue.use(VueTelInput, options); // Define default global options here (optional)
```

> View all available options in [Props](https://github.com/gotedo/vue-tel-input#props).

Or use the component directly:

```html
<!-- your-component.vue-->
<template>
  <vue-tel-input v-model="value"></vue-tel-input>
</template>
<script>
  import { VueTelInput } from '@gotedo/vue-tel-input';

  export default {
    components: {
      VueTelInput
    }
  };
</script>

<style src="@gotedo/vue-tel-input/dist/vue-tel-input.css"></style>
```

### Use as a custom field of [vue-form-generator](https://github.com/vue-generators/vue-form-generator)

- Add a component using `vue-form-generator`'s `abstractField` mixin

  ```html
  <!-- tel-input.vue -->
  <template>
    <vue-tel-input v-model="value"></vue-tel-input>
  </template>

  <script>
    import { abstractField } from 'vue-form-generator';

    export default {
      name: 'TelephoneInput',
      mixins: [abstractField]
    };
  </script>
  ```

- Register the new field as a global component

  ```js
  import Vue from 'vue';
  import TelInput from '<path>/tel-input.vue';

  Vue.component('field-tel-input', TelInput);
  ```

- Now it can be used as `tel-input` in schema of `vue-form-generator`

  ```js
  var schema: {
    fields: [
      {
        type: 'tel-input',
        label: 'Awesome (tel input)',
        model: 'telephone'
      }
    ]
  };
  ```

  Read more on `vue-form-generator`'s [instruction page](https://icebob.gitbooks.io/vueformgenerator/content/fields/custom_fields.html)

### Component lazy loading

Since the library is about 200kb of JavaScript and 100kb of CSS in order to improve initial page loading time you might consider importing it asynchronously only when user navigates to the page where the library is actually needed. The technique is called [Lazy Load](https://webpack.js.org/guides/lazy-loading/) and you can use it in some modern bundlers like Webpack and Rollup.

```html
<!-- your-component.vue-->
<template>
  <vue-tel-input v-model="value"></vue-tel-input>
</template>
<script>
  const VueTelInput = () =>
    Promise.all([
      import(
        /* webpackChunkName: "chunk-vue-tel-input" */ '@gotedo/vue-tel-input'
      ),
      import(
        /* webpackChunkName: "chunk-vue-tel-input" */ '@gotedo/vue-tel-input/dist/vue-tel-input.css'
      )
    ]).then(([{ VueTelInput }]) => VueTelInput);

  export default {
    components: {
      VueTelInput
    }
  };
</script>
```

As you see, we don't use Vue SFC `<style></style>` tag here to import component's css as it would result in CSS going to the main/vendors bundle instead of being downloaded on demand.

## Development

Clone the project

```bash
  git clone https://github.com/gotedo/vue-tel-input.git
```

Go to the project directory

```bash
  cd vue-tel-input
```

Install dependencies

```bash
  npm install
  cd docs && npm ci
```

Start the server

```bash
  npm run serve
```

## License

Copyright (c) 2018 Steven Dao.
Released under the [MIT License](https://github.com/gotedo/vue-tel-input/blob/master/LICENSE).
