<template>
  <nav v-if="user">
    <div>
      <p>Hey there {{ user.displayName }}</p>
      <p class="email">Currently logged in as {{ user.email }}</p>
    </div>
    <p class="error">{{ error }}</p>
    <button @click="handleClick">Logout</button>
  </nav>
</template>

<script>
import useLogOut from '../composables/useLogout'
import getUser from '../composables/getUser'
export default {
  setup() {
    const { logout, error } = useLogOut()
    const { user } = getUser()

    async function handleClick() {
      await logout()
      if (!error.value) {
        console.log('user logout')
      }
    }

    return {
      handleClick,
      error,
      user
    }
  }
}
</script>

<style>
nav {
  padding: 20px;
  overflow: hidden;
  border-bottom: 1px solid #eee;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
nav p {
  margin: 2px auto;
  font-size: 16px;
  color: #444;
}
nav p.email {
  font-size: 14px;
  color: #999;
}
</style>
<style lang="scss" scoped></style>
