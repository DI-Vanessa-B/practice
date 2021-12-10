<template>
<div class="wrapper">
  <h1>{{title}}</h1>
    <div class="grid-list">
    <figure v-for="image, index in images" :key="index" :class="image.size">
      <img :src="`/img/${image.path}`" alt="">
    </figure>
  </div>
</div>
</template>

<script>
const images = require('~/assets/data/images.json')
export default {
  data() {
    return{
      title: 'Welcome to the front page',
      images: images,
    }
  },
  async created() {
		const response = await this.$axios.get('https://jsonplaceholder.typicode.com/photos')
		this.images = response
	},
  }
</script>

<style>
h1 {
  font-size: 3vh;
  font-weight: bold;
}

.grid-list{
  @apply grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-3
}

figure.small {
  width: 100%;
  column-span: 2;
}

figure.medium {
  width: 100%;
  column-span: 4;
}

figure.large {
  width: 100%;
}

</style>