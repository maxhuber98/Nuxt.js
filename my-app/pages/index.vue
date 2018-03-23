<template>
  <section>
    <div class="post-container" v-for="item in posts" :key="item.id">
      <div class="post">
        <h2 class="post__header text-center">{{ item.title }}</h2>
        <div class="post__image-placeholder">
          <img src="http://source.unsplash.com/800x500" class="post__image-placeholder--image">
        </div>
        <p class="post__body">{{ item.body }}</p>
        <nuxt-link class="btn btn-default pull-right"  :to="'/details/' + item.id">Read more</nuxt-link>
      </div>
    </div>
  </section>
</template>

<script>
import Axios from 'Axios'

export default {
	data() {
		return {
			posts: []
		}
	},
	created() {
		this.fetchData()
	},
	methods: {
		fetchData() {
			Axios.get('https://jsonplaceholder.typicode.com/posts').then(response => {
				this.posts = response.data
			})
		}
	}
}
</script>
