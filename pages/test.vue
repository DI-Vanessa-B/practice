<template>
	<div class="images">
		<figure v-for="image, index in images" :key="index">
		<img :src="image.thumbnailUrl" :alt="image.title">
		<figcaption>{{index}}, {{image.title}}</figcaption>
		</figure>
	</div>
</template>

<script>
export default {
    data() {
        return {
            images: []
        }
        
    },
	async created() {
		//console.log(i am created)
		const response = await this.$axios.get('https://jsonplaceholder.typicode.com/photos', {
			params: {
				_limit: 120
			}
		})
		this.images = response.data
	},
}
</script>