<template>
  <div class="login-container">
    <form @submit.prevent="login" class="login-form">
      <h2>Log In</h2>
      <div class="email-container">
        <label>Email address</label>
        <input
          v-model="email"
          type="email"
          name="email"
          placeholder="hello@magic.link"
          required
          class="email-input"
        />
      </div>
      <button type="submit" name="button">Send Magic Link</button>
    </form>
  </div>
</template>

<script>
import { ref } from "vue";
// import Vuex store
import { useStore } from "vuex";
export default {
  setup() {
    // create new store instance
    const store = useStore();

    const email = ref("");

    // dispatch the signup action to log in the user
    const login = () => {
      store.dispatch("login", {
        email: email.value
      });
    };

    return {
      email,
      login,
    };
  },
};
</script>

<style scoped>
.login-form,
.email-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
.email-container {
  margin-bottom: 30px;
}
.email-container label {
  margin-right: auto;
  margin-bottom: 7px;
  font-size: 13px;
}
.email-container .email-input {
  width: 300px;
  height: 30px;
  border-radius: 5px;
  border: 1px solid gray;
  outline: none;
  padding: 0 5px;
}
.email-input:focus {
  border: 1px solid #0228af;
}
</style>