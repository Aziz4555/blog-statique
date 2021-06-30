<template>
    <div class="container">
        <h2>Les Articles</h2>

      <div v-for="(post,index) in posts" :key="index">
        <img :src="post.fields.couverture.fields.file.url" alt="" width="50px">
        <nuxt-link v-bind:to="post.fields.tag">{{post.fields.titre}}</nuxt-link>
      </div>
    </div>
</template>

<script>

import {createClient} from '../plugins/contentful.js'

const client=createClient()

export default {
  name: "articles",

  asyncData({env}){
    return client.getEntries({
      content_type:'post'
    }).then(entries => {
      return {posts: entries.items}
    }).catch(e => console.log(e))
  }

}
</script>

<style scoped>

</style>
