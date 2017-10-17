<template>
  <div class="hello">
    <h1>Titel: {{ post.title }}</h1>
    <p>Tekst:{{ post.body }}</p>
  </div>
  
</template>
<script>
  import axios from 'axios'
  export default {
    name: 'read-article',
    data () {
      return {
        msg: 'Read',
        post: {
          title: '',
          body: ''
        }
      }
    },
    created () {
      axios
      .get('http://cmsdev.localhost/node/5?_format=hal_json')
      .then(response => {
        this.post.title = response.data.title[0].value
        this.post.body = response.data.body[0].value
      })
      .catch(({ message: error }) => {
        console.info(error)
      })
    }
  }
</script>
