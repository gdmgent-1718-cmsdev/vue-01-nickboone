<template >
<div id="app">
  <ul v-if="posts && posts.length">
    <li v-for="post of posts">
      <p><strong>{{post.title}}</strong></p>
      <p>{{post.body}}</p>
    </li>
  </ul>
  <ul v-if="errors && errors.length">
    <li v-for="error of errors">
      {{error.message}}
    </li>
  </ul>
</div>
</template>
<script>
import axios from 'axios'
export default {
  data () {
    return {
      posts: [],
      errors: []
    }
  },
  // Fetches posts when the component is created.
  created () {
    axios.get(`http://cmsdev.localhost/node/5?_format=hal_json`)
    .then(response => console.log(response.data))
    const response = axios.get(`http://cmsdev.localhost/node/5?_format=hal_json`)
    this.posts = response.data
  },
  catch (e) {
    this.errors.push(e)
  }
}
</script>
