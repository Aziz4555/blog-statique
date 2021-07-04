<template>
  <div class="block bg-green-400 text-white">

      <h1 class="text-5xl pt-12 pb-12  text-center">{{post.fields.titre}}</h1>
    <img class="w-full p-3" :src="post.fields.couverture.fields.file.url" alt="" width="50px">
      <hr>

    <div class="pb-6">
      <p class="text-xl text-justify pr-3 pl-3"> {{post.fields.body}}</p>

    <p class="text-xl text-justify pr-3 pl-3">tag : {{post.fields.tag}}</p>

      <nuxt-link class="block text-white w-2/5 mr-auto ml-auto text-center border border-solid border-green-800  pt-3 pb-3 pr-12 pl-12 rounded-2xl bg-green-800" id="retour" v-bind:to="post.fields.tag">
        <span>Retour</span>
      </nuxt-link>

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

#retour:hover{
  animation: plusAnim 1.5s linear;
}

@keyframes plusAnim {
  50% {
    transform: scale(1.2);
  }

  100% {
    transform: scale(1);
  }

}


</style>
