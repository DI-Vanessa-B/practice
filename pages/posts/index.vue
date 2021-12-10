<template>
	<div class="posts">
		<ul>
			<li v-for="post, index in posts" :key="index" >
				<nuxt-link :to="`/posts/${post.id}`">{{post.title}}</nuxt-link>
			</li>
		</ul>

	</div>
</template>

<script>
export default {
	data() {
		return {
			posts: []
		}
	},
	async created() {
		const response = await this.$axios.get('https://jsonplaceholder.typicode.com/posts', {
			params: {
				_limit: 5
			}
		})
		this.posts = response.data
	},
}
</script>