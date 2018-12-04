<template>
  <div class="container">
    <nuxt-link to="/" class="link">Главная</nuxt-link> /
    <nuxt-link to="/video" class="link">Voximplant</nuxt-link>
    <nuxt />
  </div>
</template>

<style>
html {
  font-family: "Source Sans Pro", -apple-system, BlinkMacSystemFont, "Segoe UI",
    Roboto, "Helvetica Neue", Arial, sans-serif;
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
.link {
  color: #103d97;
}
.nuxt-link-exact-active {
  color: #000;
  font-weight: 700;
}
</style>
