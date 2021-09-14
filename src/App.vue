<template>
  <div id="nav">
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link> |
    <router-link v-if="!user" to="/login">Login</router-link> |
    <router-link to="/dashboard">Dashboard</router-link>
  </div>
  <router-view/>
</template>

<script>
import { useStore } from "vuex";
import { computed } from "vue";
export default {
  setup() {
     const store = useStore();

    const user = computed(() => store.state.user);

    return{
      user
    }
  },
}
</script>

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

button {
  width: 300px;
  height: 30px;
  padding: 0 5px;
  background-color: #35aa58;
  border: none;
  border-radius: 5px;
  color: #fff;
  cursor: pointer;
}

button:hover {
  background-color: #35aa58b7;
}
</style>
