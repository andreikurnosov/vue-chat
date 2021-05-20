<template>
  <nav>
    <div>
      <p>Hey there... display name here</p>
      <p class="email">Currently logged in as... email</p>
    </div>
    <p class="error">{{ error }}</p>
    <button @click="handleClick">Logout</button>
  </nav>
</template>

<script>
import useLogOut from '../composables/useLogout'
export default {
  setup() {
    const { logout, error } = useLogOut()

    async function handleClick() {
      await logout()
      if (!error.value) {
        console.log('user logout')
      }
    }

    return {
      handleClick,
      error
    }
  }
}
</script>

<style>
nav {
  padding: 20px;
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
