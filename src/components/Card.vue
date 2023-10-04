<template>
  <div class="container">
    <img :src="`https://xsgames.co/randomusers/assets/avatars/female/${id}.jpg`" alt="avatar">
    <p>Name: {{ title }}</p>
    <p>Email: {{ email }}</p>
    <p>Username: {{ username }}</p>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
 name: 'Card',
  props: {
    id: {
      type: Number,
      required: true
    },
    title: {
      type: String,
      required: true
    },
    email: String,
    username: String,
  }
});
</script>

<style scoped>
  .container {
    display: flex;
    flex-direction: column;
  }

  p {
    margin: 0;
    font-size: smaller;
  }
</style>