<template>

  <div class="bg-green-400 h-screen" id="container">
    <h1 class="text-5xl text-white text-center pt-12 pb-12 ">L'auteur</h1>
    <div class="grid grid-cols-2" id="presentation">
      <img class="w-full" :src="post.fields.photo.fields.file.url" alt="" width="50px">
<!--      <p class="text-gray-300">{{post.fields.title}}</p>-->
      <p class="text-white text-justify pl-3 pr-3">{{post.fields.description}}</p>
    </div>

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

@media screen and (max-width:768px) {

    #container{
      @apply h-full
    }
    #presentation{
      @apply grid-cols-1
    }

}


</style>
