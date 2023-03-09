<script setup>
import stytch from '../stytch'
let user = stytch.user.getSync()
let session = stytch.session.getSync()

function logout() {
  stytch.session.revoke()
}
</script>
<template>
  <div class="container">
    <div class="card">
      <h1>Profile</h1>
      <h2>User object</h2>
      <pre class="code-block">{{ user }}</pre>

      <h2>Session object</h2>
      <pre class="code-block">{{ session }}</pre>
      <p>
        You are logged in, and a Session has been created. The SDK stores the Session as a token and
        a JWT in the browser cookies as
        <span class="code">stytch_session</span> and
        <span class="code">stytch_session_jwt</span> respectively.
      </p>
      <button @click="logout" class="primary">Log out</button>
    </div>
  </div>
</template>
