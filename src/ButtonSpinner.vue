<template>
	<button 
	:disabled="disabled" 
	:status="status" 
	class="btn-loader" 
	:class="{'btn-loader-error': status == 'error', 'btn-loader-success': status == 'success'}">

	<transition name="fade" mode="out-in">
		<div v-if="isLoading && status == ''" class="spinner"></div>
		<div v-if="status == 'success'" class="check"></div>
		<div v-if="status == 'error'" class="cross"></div>
	</transition>

	<slot v-if="status == ''"></slot>
</button>

</template>

<script>
	export default {
		name: 'loading-button',
		props: {
			id:{
				type: String,
				default: ''
			},
			isLoading: {
				type: Boolean,
				default: false
			},
			type: {
				type: String,
				default: "button"
			},
			disabled: {
				type: Boolean,
				default: false
			},
			status: {
				type: String,
				default: ''
			}
		},
	};
</script>

<style lang="css" scoped>

	.fade-enter-active, .fade-leave-active { transition: opacity 1s; }
	.fade-enter, .fade-leave-active { opacity: 0; }


	@-webkit-keyframes rotation {
		from {
			-webkit-transform: rotate(0deg)
		}

		to {
			-webkit-transform: rotate(359deg)
		}
	}

	@-moz-keyframes rotation {
		from {
			-moz-transform: rotate(0deg)
		}

		to {
			-moz-transform: rotate(359deg)
		}
	}

	@-o-keyframes rotation {
		from {
			-o-transform: rotate(0deg)
		}

		to {
			-o-transform: rotate(359deg)
		}
	}

	@keyframes rotation {
		from {
			transform: rotate(0deg)
		}

		to {
			transform: rotate(359deg)
		}
	}

	.btn {
		display: inline-block;
		font-weight: 400;
		line-height: 1.25;
		text-align: center;
		white-space: nowrap;
		vertical-align: middle;
		cursor: pointer;
		-webkit-user-select: none;
		-moz-user-select: none;
		-ms-user-select: none;
		user-select: none;
		border: 1px solid transparent;
		padding: .5rem 1rem;
		font-size: 1rem;
		border-radius: .25rem;
	}
	
	button.btn-loader {
		display: flex;
		align-items: center;
		transition: .3s all ease;
	}

	button.btn-loader-error { background-color: #F44336; }
	button.btn-loader-success { background-color: #8BC34A; }
	button.btn-loader:disabled { cursor: not-allowed; }

	/**
		Spinner Icon
	**/

	.spinner {
		height: 16px;
		width: 16px;
		margin-right: 2px;
		opacity: 1;
		filter: alpha(opacity=100);
		-webkit-animation: rotation .7s infinite linear;
		-moz-animation: rotation .7s infinite linear;
		-o-animation: rotation .7s infinite linear;
		animation: rotation .7s infinite linear;
		border-left: 4px solid rgba(0,0,0,0.2);
		border-right: 4px solid rgba(0,0,0,0.2);
		border-bottom: 4px solid rgba(0,0,0,0.2);
		border-top: 4px solid #9E9E9E;
		border-radius: 100%;
		transition: .3s all ease;
	}


	/**
		Check Icon
	**/
	
	.check {
		display:inline-block;
		width: 22px;
		height:22px;
		/*background: #8BC34A;*/
		border-radius:50%;
		-ms-transform: rotate(45deg); 
		-webkit-transform: rotate(45deg); 
		transform: rotate(45deg);
	}

	.check:before{
		content:"";
		position: absolute;
		width:3px;
		height:9px;
		background-color:#fff;
		left:11px;
		top:6px;
	}

	.check:after{
		content:"";
		position: absolute;
		width:3px;
		height:3px;
		background-color:#fff;
		left:8px;
		top:12px;
	}	

	/**
		Cross Icon
	**/

	.cross {
		display: inline-block;
		width: 16px;
		height: 16px;
		position: relative;
	}

	.cross:before, .cross:after {
		position: absolute;
		left: 8px;
		content: ' ';
		height: 17px;
		width: 2px;
		background-color: #fff;
	}
	.cross:before {
		-moz-transform: rotate(45deg);
		-ms-transform: rotate(45deg);
		transform: rotate(45deg);
	}
	.cross:after {
		-moz-transform: rotate(-45deg);
		-ms-transform: rotate(-45deg);
		transform: rotate(-45deg);
	}
</style>