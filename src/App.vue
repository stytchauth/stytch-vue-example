<script setup>
import { onBeforeUnmount } from 'vue'
import { RouterView } from 'vue-router'
import stytch from './stytch'
import router from './router'
/*
Session logic

The logic below listens to changes on the Stytch Session to:
- redirect newly authenticated traffic to /profile.
- redirect the user to login view if they log out.
*/
const unsubscribe = stytch.session.onChange((session) => {
  console.log('ONCHANGE', session)
  if (session) {
    router.push({ name: 'profile' })
  } else {
    router.push({ name: 'login' })
  }
})

onBeforeUnmount(() => {
  unsubscribe && unsubscribe()
})
</script>

<template>
  <RouterView />
</template>
