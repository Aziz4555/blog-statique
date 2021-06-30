<template>
  <div>
    <img :src="post.fields.couverture.fields.file.url" alt="" width="50px">
    <h1>Le titre de l'article</h1>
      <h3>{{post.fields.titre}}</h3>
      <hr>
    <p>
      <nuxt-link to="/">retour</nuxt-link>
    </p>
    <div class="content">
      <h1>Le contenu de l'article</h1>
      {{post.fields.body}}
    </div>
  </div>
</template>

<script>
import {createClient} from '../plugins/contentful.js'

const client=createClient()

export default {
  asyncData({params}){
    return client.getEntries({
        content_type:'post',
        'fields.tag':params.tag
      }).then(entries => {
        return {post:entries.items[0]}
      }).catch(console.error)
  },
}
</script>

<style scoped>

</style>
