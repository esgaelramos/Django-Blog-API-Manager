<template>
  <div class="blog">
    <h1>This is a Blog View</h1>
    <div v-for="posts in APIData" :key="posts.id" class="item">
      <hr>
      <router-link :to="{ name: 'BlogPost', params: { id: posts.id, title: posts.title, thumbnail: posts.thumbnail, slug: posts.slug, excerpt: posts.excerpt, content: posts.content }}">
      <h3>{{ posts.title }}</h3>
      </router-link>
      <p>
        {{ posts.content }}
      </p>
    </div>
  </div>
</template>
<script>
import { getAPI } from '../axios-api'

export default {
  name: 'Blog',
  data(){
    return {
      APIData: []
    }
  },  
  created () {
    getAPI('/blog/posts/',)
      .then(response => {
        console.log('Post API has recieved data')
        this.APIData = response.data
      })
      .catch(err => {
        console.log(err)
      })
  }
}
</script>