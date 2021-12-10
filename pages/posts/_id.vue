<template>
  <div class=“post”>
    <nuxt-link to=“/”>Back to posts</nuxt-link>
    <button class=“border” @click='handleBack'>Go back in history</button>
    <h1>{{ post.title }}</h1>
    <div>{{ post.body }}</div>
  </div>
</template>
<script>
export default {
  async asyncData({ params, $axios }) {
    const post = await $axios.$get(
      `https://jsonplaceholder.typicode.com/posts/${params.id}`
    );
    return { post };
  },
  methods: {
    handleBack() {
      this.$router.go(-1);
    },
  },
};
</script>
