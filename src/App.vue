<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link>
      |
      <router-link to="/about">About</router-link>
      <br />
      <router-link to="/index">Actors Index</router-link>
      |
      <router-link to="/moviesindex">Movies Index</router-link>

      <Br />
      <router-link to="/signup">Signup</router-link>
      <br />
      <br />
      <router-link to="/login">Login</router-link>
      |
      <router-link to="/logout">Logout</router-link>
      <br />
      <br />
    </div>
    <router-view />
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

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
