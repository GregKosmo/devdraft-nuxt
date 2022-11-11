<template>
  <div>
    Welcome to DevDraft
    <span v-if="$auth.loggedIn">, {{ $auth.user.name }}</span>
    !
    <button v-if="!$auth.loggedIn" @click="$auth.loginWith('github')">
      Log In
    </button>
    <div v-if="$auth.loggedIn">
      <nuxt-link to="home">My Teams</nuxt-link>
    </div>
    <button v-if="$auth.loggedIn" @click="$auth.logout()">
      Log Out
    </button>
  </div>
</template>

<script lang="ts">
export default {};
</script>
