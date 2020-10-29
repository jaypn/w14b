<template>
  <div id="app">
    <div id="nav">
      <router-link to="/login">Login</router-link>
      <!-- <router-link to="/game">Game</router-link> -->
    </div>
    <router-view />
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
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

.btn {
    background-color: #008CBA;
    color: white;
    padding:10px 8px;
    border-radius: 10px;
    border: none;
    width: 80px;
    margin-top: 8px;
    margin-left: 4px;
    margin-right: 4px;
    text-decoration: none;
    font-weight: 700;
}

.btn:hover {
    background-color: #035f7e;
    cursor: pointer;
}
</style>