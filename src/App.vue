<template>
  <div id="app">
    <header class="navbar is-info">
      <div class="container">
        <div class="navbar-brand title">FFS</div>
        <div class="navbar-start">
          <router-link to="/" class="navbar-item">Home</router-link>
          <router-link to="/about" class="navbar-item">About</router-link>
          <router-link to="/survey" class="navbar-item">Servey</router-link>
        </div>
      </div>
    </header>
    <router-view />
    <footer class="footer"><p>© All rights reserved by UD.</p></footer>
  </div>
</template>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

.router-link-exact-active {
  color: #42b983;
}

header {
  margin-bottom: 40px;
}

.navbar-brand {
  margin-bottom: 0px;
  padding: 8px 12px;
}
</style>
