# VueButtonSpinner
[![npm version](https://badge.fury.io/js/vue-button-spinner.svg)](https://badge.fury.io/js/vue-button-spinner)

> Simple VUE 2 component to create a button spinner. The perfect solution for your submit buttons!

![alt tag](https://ibin.co/31v55OGl4kwc.gif)

# Features

- Show an css loader into the button to indicate the request status.
- Add a custom html inside the component.
- Pure CSS loaders, no fonts or images have been used.
- Different styles for each state: loading, success, error.

# Install

```npm install vue-button-spinner```

# Usage

### Example:

[Your .vue component (vue-loader with webpack or use vue-cli projects)]
```js

import ButtonSpinner from 'vue-button-spinner';

export default {
		name: 'events-form',
		data() {
			return {
				isSubmitted: false,
				isSent: false,
				isValid: null,
				status: ''
			}
		},
		components: {	
			'button-spinner': ButtonSpinner
		},
		methods: {
			onSubmit() {
				$someRequest('/url', 'GET')
				.then(response => {
					this.isSent = true;
					this.status = 'success';
				})
				.catch(error => {
					console.error(error);
					this.isSent = false;
					this.status = 'error';
				});

				this.isSubmitted = true;
			}
		}
}

```

[Your HTML code]
```html

<button-spinner 
	type="submit" 
	class="btn btn-default" 
	:isLoading="isSubmitted && !isSent" 
	:disabled="isSent"
	:status="status">
	<span>Submit</span>
</button-spinner>

```

# License

MIT