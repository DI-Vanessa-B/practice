<template>
<div class="wrapper">
  <h1>{{title}}</h1>
    <div class="grid-list">
    <figure v-for="image, index in images" :key="index" :class="image.size">
      <p>{{image}}</p>
      <img :src="`/img/${image.path}`" alt="">
      <p>{{image.size}}, {{image.hasChildren}}</p>
    </figure>
  </div>
</div>
</template>

<script>
const images = require('~/assets/data/images.json')
export default {
  data() {
    return{
      title: 'Welcome',
      images: images,
    }
  }
}
</script>

<style>
h1 {
  font-size: 3vh;
  font-weight: bold;
}

.grid-list{
  @apply grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-12
}

figure.small {
  border: 10px solid red;
  width: 100%;
  column-span: 2;
}

figure.medium {
  border: 10px solid blue;
  width: 100%;
  column-span: 4;
}

figure.large {
  border: 10px solid yellow;
  width: 100%;
}

</style>