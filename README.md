# @mathewparet/vue-pin-input

> A Vue.JS PIN input. This data entered will be masked like a password.

## Installation

``` bash
# install
npm install @mathewparet/vue-pin-input
```

## Initialization
```js
import PinInput from '@mathewparet/vue-pin-input';
Vue.use(PinInput);
```

## Usage
```html
	<pin-input type="number" v-model="pin">
```

Attribute | Value | Default | Description |
--- | --- | --- | --- |
type | ```string``` or ```number``` | number | Type of data to accept |