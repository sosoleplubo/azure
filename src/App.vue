<template>
  <div>
    <h1>Utilisateurs test</h1>
    <ul>
      <li v-for="u in users" :key="u.Id">
        {{ u.Nom }} – {{ u.Email }}
      </li>
    </ul>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const users = ref([])

onMounted(async () => {
  const res  = await fetch('https://backend-miniapp-sf.azurewebsites.net/api/users')
  users.value = await res.json()
})
</script>
