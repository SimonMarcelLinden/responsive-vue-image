<h1 align="center">responsive-vue-image</h1>

[![Latest Version on NPM](https://img.shields.io/npm/v/responsive-vue-image.svg?style=flat-square)](https://www.npmjs.com/package/responsive-vue-image)
[![Software License](https://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat-square)](LICENSE.md)
[![npm](https://img.shields.io/npm/dt/responsive-vue-image?style=flat-square)](https://www.npmjs.com/package/responsive-vue-image)


> Vue Component for responsive (desktop, tablet and mobile) images elements with fallback image.
# responsive-vue-image

## Install and basic usage
Install via NPM...
```
npm i -s responsive-vue-image
```

Register the component:
```
import Vue from 'vue'
import ResponsiveImage from 'responsive-vue-image';

Vue.component('ResponsiveImage', ResponsiveImage);
```
Use the component:

```
<template>
  <div id="app">
    <ResponsiveImage />
  </div>
</template>

<script>
import ResponsiveImage from 'responsive-vue-image';

export default {
  name: 'App',
  components: {
    ResponsiveImage
  }
}
</script>
```

### Props

#### fallbackImage
Type: `String`<br>
Required: `false`<br>
Default: `https://via.placeholder.com/64`

Fallback image which is loaded if the loaded image is not available.


#### image
Type: `Object`<br>
Required: `false`<br>
Default: 
```javascript
{
    imageMobile : 'https://via.placeholder.com/128', // Image for mobile media view
    imageTablet : 'https://via.placeholder.com/256', // Image for tablet media view    
    image       : 'https://via.placeholder.com/512', // Image for desktop media view
    alt         : 'Default Image'                    // Image for mobile
}
```

The alt attribute provides alternative information for the image if a user is still unable to view it for some reason (a slow connection, an error in the src attribute, or if the user is using a screen reader).


## Contributing

Any contribution to the code or any part of the documentation and any idea and/or suggestion are very welcome.

``` bash
# serve with hot reload at localhost:8081
npm run start

# distribution build
npm run build

```

## License

[MIT license](LICENSE)
