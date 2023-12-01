<script lang="ts">
import axios from 'axios';
export default {
  props: ['msg'],

  data() {
    return {
      posts: [] as any[]
    }
  },

  mounted() {
    axios
    .get('http://localhost:3000/api/posts')
    .then((response) => {
      console.log('response', response);
      this.posts = response.data
    })
  }
}
</script>

<template>
  <div class="message">
    <h1>{{ msg }}</h1>
  </div>
  <ul class="post-list">
    <li
      v-for="post in posts"
      :key="post.id"
      class="post"
    >
      {{ post.title }}
    </li>
  </ul>
</template>

<style scoped></style>
