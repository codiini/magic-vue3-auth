<template>
  <div class="dashboard-container">
    <h2>Welcome to our Dashboard Page</h2>
    <!-- use the value of data in the template -->
    <p>Hello {{user.email}}!</p>
    <p>{{user.publicAddress}}</p>
    <button @click="logout">Sign out</button>
  </div>
</template>

<script>
// Import Vuex and Computed
import { useStore } from "vuex";
import { computed } from "vue";
export default {
  setup() {
    // create store instance
    const store = useStore();

    // fetch the value of logged in user from the Vuex store
    const user = computed(() => store.state.user);

    const logout = () => {
      // dispatch the logout action to logout user
      store.dispatch("logout");
    };

    return {
      logout,
      user
    };
  },
};
</script>

<style scoped>
</style>