<template>
  <div @scroll="scrollHandler">
    <mainmenu/>
    <nuxt/>
  </div>
</template>

<script>
import $ from 'jquery'

export default {
	methods: {
		scrollHandler() {
			var offsetY = window.pageYOffset

			if (offsetY > 55) {
				$('.menu').addClass('menu--sticky')
				$('.content').addClass('padding-top')
			} else {
				$('.menu').removeClass('menu--sticky')
				$('.content').removeClass('padding-top')
			}
		}
	},
	created() {
		if (process.browser) {
			window.addEventListener('scroll', this.scrollHandler)
		}
	},
	destroyed() {
		if (process.browser) {
			window.removeEventListener('scroll', this.scrollHandler)
		}
	}
}
</script>

<style>
html {
	font-family: 'Source Sans Pro', -apple-system, BlinkMacSystemFont, 'Segoe UI',
		Roboto, 'Helvetica Neue', Arial, sans-serif;
	font-size: 16px;
	word-spacing: 1px;
	-ms-text-size-adjust: 100%;
	-webkit-text-size-adjust: 100%;
	-moz-osx-font-smoothing: grayscale;
	-webkit-font-smoothing: antialiased;
	box-sizing: border-box;
}

*,
*:before,
*:after {
	box-sizing: border-box;
	margin: 0;
}
</style>
