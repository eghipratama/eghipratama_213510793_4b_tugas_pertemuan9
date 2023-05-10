<template>
  <nav>
    <router-link to="/">Home</router-link> |
    <router-link :to="{ name: 'About' }">About</router-link> |
    <router-link :to="{ name: 'Todo' }">Todo</router-link>
  </nav>
  <router-view/>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
  text-decoration: none;
  padding: 10px;
  border-radius: 4px;
}

nav a.router-link-exact-active {
  color: white;
  background: rgba(255, 0, 0, 0.75);
}

body {
  background-image: url("https://www.slideteam.net/media/catalog/product/cache/960x720/0/9/0914_red_pen_writing_agenda_for_business_stock_photo_Slide01.jpg");
  background-size: 100%100%;
  background-attachment: fixed;
}

</style>
