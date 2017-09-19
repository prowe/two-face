<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    
    <a href="#" v-if="!loggedIn" v-on:click="onLogin">Login</a>
    <router-link v-if="loggedIn" to="/private">Go to Private Side</router-link>
    <a href="#" v-if="loggedIn" v-on:click="onLogout">Logout</a>
  </div>
</template>

<script>
export default {
  name: 'hello',
  methods: {
    onLogin() {
      // eslint-disable-next-line
      console.log(`logging in..In a real app you would pop an OpenID Connect modal, redirect to a login page, etc. 
        Here we're just setting a hard coded cookie to true`);
      document.cookie = 'two-face-auth=true;path=/';
      this.loggedIn = true;
    },
    onLogout() {
      document.cookie = 'two-face-auth=false;path=/';
      this.loggedIn = false;
    },
  },
  data() {
    return {
      loggedIn: false,
      msg: 'Welcome to Your Vue.js App',
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
