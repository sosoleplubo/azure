<template>
  <div>
    <h1>Utilisateurs</h1>
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
  const res  = await fetch(`${import.meta.env.VITE_API_BASE}/api/users`)
  users.value = await res.json()
})
</script>
