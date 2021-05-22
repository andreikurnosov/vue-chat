<template>
  <div class="container">
    <navbar />
    <new-chat-form />
  </div>
</template>

<script>
import { watch } from 'vue'
import { useRouter } from 'vue-router'
import getUser from '../composables/getUser'
import Navbar from '../components/Navbar.vue'
import NewChatForm from '../components/NewChatForm.vue'

export default {
  components: {
    Navbar,
    NewChatForm
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
