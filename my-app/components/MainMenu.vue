<template>
  <nav class="menu">
    <ul class="menu__bar menu__bar--left">
      <li class="menu__link"><nuxt-link class="menu__link--anchor" to="/">Home</nuxt-link></li>
    </ul>
    <ul class="menu__bar menu__bar--middle">
      <li class="menu__logo"><h3>My-app</h3></li>
    </ul>
    <ul class="menu__bar menu__bar--right">
      <li class="menu__link">About</li>
    </ul>
  </nav>
</template>

<script>
export default {
	name: 'mainmenu'
}
</script>
