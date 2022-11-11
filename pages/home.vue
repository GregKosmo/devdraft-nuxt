<template>
  <div>
    <div>
      <button @click="$auth.logout()">
        Log Out
      </button>
    </div>
    <div v-for="user in users" :key="user.id" class="profile">
      <img class="profile-image" :src="user.avatar_url" />
      <div>
        {{ user.login }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  middleware: "auth",
  async asyncData({ $axios }) {
    const users = await $axios.get("https://api.github.com/users");

    return {
      users: users.data
    };
  }
};
</script>

<style>
.profile {
  display: inline-block;
  margin: 16px;
}
.profile img {
  width: 100px;
}
</style>
