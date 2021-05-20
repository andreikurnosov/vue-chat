<template>
  <form @submit.prevent="handleSubmit">
    <input
      type="text"
      required
      placeholder="display name"
      v-model="displayName"
    />
    <input type="email" required placeholder="email" v-model="email" />
    <input type="password" required placeholder="password" v-model="password" />

    <button>Sign Up</button>
  </form>
</template>

<script>
import { ref } from 'vue'
import useSingUp from '../composables/useSignUp'

export default {
  setup() {
    const { error, signup } = useSingUp()

    const displayName = ref('')
    const email = ref('')
    const password = ref('')

    async function handleSubmit() {
      await signup(email.value, password.value, displayName.value)
      console.log('user signed up ')
    }

    return {
      displayName,
      email,
      password,
      handleSubmit
    }
  }
}
</script>

<style scoped></style>
