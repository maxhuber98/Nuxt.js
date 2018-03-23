<template>
  <section class="content">
    <div class="post-container" v-for="item in posts" :key="item.id">
      <div class="post">
        <h2 class="post__header text-center">{{ item.title }}</h2>
        <div class="post__image-placeholder">
          <content-loader :unique-key="uniqueKey" v-show="!loaded" :width="800" :height="400"></content-loader>
          <img :src="'http://source.unsplash.com/800x400'" class="post__image-placeholder--image" @load="setDone">
        </div>
        <p class="post__body">{{ item.body }}</p>
        <nuxt-link class="btn btn-default pull-right"  :to="'/details/' + item.id">Read more</nuxt-link>
      </div>
    </div>
  </section>
</template>

<script>
import Axios from 'Axios'
import { ContentLoader } from 'vue-content-loader'

export default {
	components: {
		ContentLoader
	},
	asyncData() {
		const uid = Math.random()
			.toString(36)
			.substring(2)
		return {
			uniqueKey: uid
		}
	},
	data() {
		return {
			posts: [],
			loaded: false
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
		},
		setDone() {
			this.loaded = true
			console.log('test')
		}
	}
}
</script>
