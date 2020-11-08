<template>
  <div id="app">
    <div id="nav">
      <router-link class="nav-item" to="/">
      <div class="menu-item">
        <p>Home</p>
      </div>
      </router-link>
      <router-link class="nav-item" to="/search">
        <div class="menu-item">
          <p>Search</p>
        </div>
      </router-link>
      <router-link class="nav-item" to="/watchlist">
        <div class="menu-item">
          <p>My Friends</p>
        </div>
      </router-link>
    </div>
    <hr>
    <router-view/>
    <div class="footer-padding"></div>
    <div class="footer">
      <a href="https://github.com/AmmonWarnick/creative3">GitHub</a>
    </div>
  </div>
</template>

<script>
export default {
  computed: {
    watchlistSize() {
      if (this.$root.$data.watchlist.length === undefined) {
        return 0;
      }
      else {
        return this.$root.$data.watchlist.length;
      }
    }
  }
}
</script>

<style>

* {
  margin: 0;
  padding: 0;
}

body, html {
  min-height: 100vh;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: white;
  background-color: lightgrey;
  min-height: 100vh;
  margin-right: 9em;
}

#nav {
  padding: 1em;
  display: flex;
  justify-content: flex-end;
  vertical-align: center;
  background-color: grey;
}

#nav a {
  font-weight: bold;
  color: white;
  text-decoration: none;
}

#nav a.router-link-exact-active {
  color: green;
}

.nav-item {
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 1.5em;
  margin-left: 1em;
}

i {
  font-size: 2em;
}

#watchlistCount {
    font-size: 0.8em;
    background: #e31502;
    color: #fff;
    padding: 0 5px;
    vertical-align: 1.2em;
    margin-left: -0.9em;
}

.footer-padding {
  height: 7vh;
}

.footer {
    display: flex;
    width: 100%;
    height: 7vh;
    justify-content: center;
    align-items: center;
    background-color: gray;
    box-shadow: 0px -4px 5px rgba(0, 0, 0, 0.2);
    padding: 0.3em 0em;
    bottom: 0;
  }

  .footer a {
    margin: 0em 1em;
    color: black;
    font-size: 1em;
    text-decoration: none;
    padding: 0.2em;
  }

</style>
