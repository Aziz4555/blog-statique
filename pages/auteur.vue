<template>
  <div>
    <h1>Description de l'auteur</h1>
      <img :src="post.fields.photo.fields.file.url" alt="" width="50px">
    <p>{{post.fields.title}}</p>
    <p>{{post.fields.description}}</p>

  </div>
</template>

<script>
import {createClient} from '../plugins/contentful.js'

const client=createClient()

export default {
  name: "auteur",
  asyncData({env}){

    return client.getEntries({
      content_type:'author'
    }).then(entries => {
      return {post:entries.items[0]}
    }).catch(console.error)

  }

}
</script>

<style scoped>

</style>
