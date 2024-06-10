<script setup>
import { onMounted } from 'vue'
import stytch from '../stytch'
import { Products } from '@stytch/vanilla-js'

const styles = {
  container: {
    width: '100%'
  },
  buttons: {
    primary: {
      backgroundColor: '#4A37BE',
      borderColor: '#4A37BE'
    }
  }
}

const REDIRECT_URL = 'http://localhost:3000/authenticate'
const config = {
  products: [Products.emailMagicLinks],
  emailMagicLinksOptions: {
    loginRedirectURL: REDIRECT_URL,
    loginExpirationMinutes: 60,
    signupRedirectURL: REDIRECT_URL,
    signupExpirationMinutes: 60
  }
}

/*
The Stytch JavaScript SDKs offer callbacks that help you track where users are in the authentication flow.
You can also use these callbacks to trigger actions in your application.

For example, you can use a the onEvent callback with a 200 on PASSWORD_AUTHENTICATE to trigger a redirect
to a protected page after a user successfully logs in.
*/
const callbacks = {
  onEvent: (message) => console.log(message),
  onError: (error) => console.log(error)
}

// lifecycle hooks
onMounted(() => {
  stytch.mountLogin({
    elementId: '#stytch-sdk',
    styles,
    config,
    callbacks
  })
})
</script>
<template>
  <div class="container">
    <div id="stytch-sdk"></div>
  </div>
</template>
