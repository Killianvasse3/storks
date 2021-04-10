<template>
  <div class="navig">
    <div class="side">
      <img alt="Vue logo" src="./assets/pdp.png">
      <div class="nav">
        <router-link to="/">Home</router-link>
        <router-link to="/dashboard">Dashboard</router-link>
      </div>
    </div>
    <div class="core">
      <router-view/>
    </div>
  </div>
</template>

<style>
* {
  margin: 0%;
  padding: 0%;
  background-color: #100c2a;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #00509b;
}

.nav {
  padding: 3%;
  margin-top: 30px;
  display: flex;
  justify-content: center;
  flex-direction: column;
}

.nav a {
  padding: 10%;
  margin-bottom: 5%;
  font-weight: bold;
  color: #00509b;
  text-decoration: none;
  border: solid 2px white;
  border-radius: 5px;
}

.nav a.router-link-exact-active {
  color: #ffffff;
}
.navig {
  display: flex;
  flex-direction: row;
}
.core {
  width: 86%;
}
.side img {
  transform: translate(50%);
  width: 50%;
  margin-bottom: 15%;
  margin-top: 15%;
  border-radius: 100px;
}
.side {
  display: flex;
  flex-direction: column;
  width: 13%;
  height: 90.1vh;
}
</style>
