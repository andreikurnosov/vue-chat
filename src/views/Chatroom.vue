<template>
  <div class="container">
    <navbar />
  </div>
</template>

<script>
import { watch } from 'vue'
import { useRouter } from 'vue-router'
import getUser from '../composables/getUser'
import Navbar from '../components/Navbar.vue'

export default {
  components: {
    Navbar
  },
  setup() {
    const { user } = getUser()
    const router = useRouter()

    watch(user, () => {
      if (!user.value) {
        router.push({ name: 'Welcome' })
      }
    })
  }
}
</script>
