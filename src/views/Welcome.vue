<template>
  <div class="welcome container">
    <div v-if="showLogin">
      <h2>Login</h2>
      <login-form />
      <p>
        No account yet? <span @click="showLogin = false">Signup</span> instead
      </p>
    </div>
    <div v-else>
      <h2>Sign up</h2>
      <sign-up-form />
      <p>
        Already registered?
        <span @click="showLogin = true">Login</span> instead
      </p>
    </div>
  </div>
</template>

<script>
import { ref } from 'vue'
import LoginForm from '../components/LoginForm.vue'
import SignUpForm from '../components/SignUpForm.vue'

export default {
  components: { SignUpForm, LoginForm },

  setup() {
    const showLogin = ref(true)

    return {
      showLogin
    }
  }
}
</script>

<style>
.welcome {
  text-align: center;
  padding: 20px 0;
}
p {
  letter-spacing: 5px;
  color: #333;
  font-family: sans-serif;
  font-weight: bold;
  font-size: 16px;
  margin: 5px;
}

.welcome form {
  width: 300px;
  margin: 20px auto;
}
.welcome label {
  display: block;
  margin: 20px 0 10px;
}
.welcome input {
  width: 100%;
  padding: 10px;
  border-radius: 20px;
  border: 1px solid #eee;
  outline: none;
  color: #999;
  margin: 10px auto;
}

.welcome span {
  font-weight: bold;
  text-decoration: underline;
  cursor: pointer;
}
.welcome button {
  margin: 20px auto;
}
</style>
