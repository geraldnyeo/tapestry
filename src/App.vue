<script setup lang="ts">
import { ref, onMounted } from 'vue';
import { RouterLink, RouterView } from 'vue-router';
import axios from 'axios';

const API = process.env.API_URL || "http://localhost:3000/";
const message = ref("");

const getServerResponse = async () => {
  const res = await axios.get(API);
  message.value = res.data;
}

onMounted(async () => {
  await getServerResponse();
})
</script>

<template>
  <div>
    <h1>MESSAGE FROM THE SERVER:</h1>
    <p>{{ message }}</p>

    <RouterView />
  </div>
</template>
