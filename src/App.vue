<template>
  <div>
    <h1>Utilisateurs</h1>
    <ul>
      <li v-for="user in users" :key="user.id">{{ user.name }} - {{ user.email }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      users: []
    }
  },
  mounted() {
    fetch('https://backend-miniapp-sf.azurewebsites.net/api/users')
        .then(response => response.json())
        .then(data => {
          this.users = data;
        });
  }
}
</script>
