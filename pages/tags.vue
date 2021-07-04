<template>
  <div >
    <p>{{tag_id}}</p>

    <select v-model="selected">
      <option value="">Choisissez</option>
      <option  v-for="(tag,index) in tag_id" :value="tag"  :key="index">{{tag}}</option>
    </select>

    <div class="flex" v-for="(post,index) in triePost" :key="index">
      <p>{{post.fields.titre}}</p>
    </div>

<!--    <p>{{this.posts}}</p>-->

  </div>
</template>

<script>
import {createClient} from '../plugins/contentful.js'

const client=createClient()

export default {
  name:'tags',
  data(){
    return{
      posts:[],
      tag_id:[],
      selected:""
    }
  },

  computed:{
      triePost(){
        const p=[]

        if(this.selected===""){
            return this.posts
        }else{

          for(var i=0; i<this.posts.length; i++) {
            console.log('ok')
            const unPost = this.posts[i]
            if (unPost.metadata.tags.length > 0) {
              const desTags = unPost.metadata.tags
              console.log('ok tableau')
              for (var j = 0; j < desTags.length; j++) {
                if (desTags[j].sys.id === this.selected) {
                  p.push(unPost)
                }
              }
            }
          }
          return p
        }
      }
  },

  asyncData({env}){
    return client.getEntries({
      content_type:'post'
    }).then(entries => {

      const tags=[]
      const tagid=[]
      for(var i=0; i<entries.items.length;i++){
        if(entries.items[i].metadata.tags.length>0){
          tags.push(entries.items[i].metadata.tags)
        }

      }



      for(var i=0; i<tags.length;i++) {
        for (var j = 0; j < tags[i].length; j++) {
          if(!(tagid.includes(tags[i][j].sys.id))){
            tagid.push(tags[i][j].sys.id)
          }

        }
      }

      return {posts: entries.items, tag_id:tagid}

    }).catch(e => console.log(e))
  }
}
</script>

<style scoped>

</style>
