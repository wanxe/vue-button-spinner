# VueButtonSpinner
[![npm version](https://badge.fury.io/js/vue-button-spinner.svg)](https://badge.fury.io/js/vue-button-spinner)

> Simple VUE 2 component to create a button spinner. The perfect solution for your submit buttons!

![alt tag](https://ibin.co/31v55OGl4kwc.gif)

# Features

- Show an css loader into the button to indicate the request status.
- Add a custom html inside the component.
- Pure CSS loaders, no fonts or images have been used.
- Different styles for each state: loading, success, error.
- Available props:
    * 'isLoading' (boolean) to show the spinner
    * 'status' (String | Boolean) allow 'success' or true and 'error' or false.
- **Remember use the .native modifier for the events ([docs](https://vuejs.org/v2/guide/migration.html#Listening-for-Native-Events-on-Components-with-v-on-changed))**

# Install

```npm install vue-button-spinner```

# Usage

### Example:

[Your .vue component (vue-loader with webpack or use vue-cli projects)]
```js

import VueButtonSpinner from 'vue-button-spinner';

export default {
		name: 'events-form',
		data() {
			return {
				isLoading: false,
				status: '',
			}
		},
		components: {	
			VueButtonSpinner
		},
		methods: {
			onSubmit() {
			    this.isLoading = true
				$someRequest('/url', 'GET')
				.then(response => {
					this.isLoading = false
					this.status = true // or success
					setTimeout(() => { this.status = '' }, 2000) // to clear the status :)
				})
				.catch(error => {
					console.error(error)
					this.isLoading = false
					this.status = false //or error
				})
			}
		}
}

```

[Your HTML code]
```html

<button-spinner
	:isLoading="isLoading" 
	:disabled="isLoading"
	:status="status">
	<span>Submit</span>
</button-spinner>

```
