<template>
<div id="app">
  <nav>
    <router-link to="/">Home</router-link> |
    <router-link to="/product">Product</router-link>
    <router-link to="/order/1">Order</router-link> |
    <router-link to="/contact">Contact Us</router-link>
  </nav>
  <router-view/>
</div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
}

nav {
  background-color:#222;
  padding: 15px;
  font-weight: bold;
}

nav a {

  margin: 0 15px;
  text-decoration: none;
  color: white;
}

nav a.router-link-active {
  color: #00ffcc;
}
nav a:hover {
  color: #00ffcc;
}
</style>
