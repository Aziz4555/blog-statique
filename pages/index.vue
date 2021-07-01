<template>



  <div class="bg-green-400">
    <h2 class="block text-center pt-12 pb-12 bg-green-400 text-5xl text-white ">Bienvenue !</h2>
    <h3 class="text-white text-xl pb-6 pr-3 pl-3 text-center">Tu as atterri dans un blog où on parle football, ce sport possède la communauté de passionné la plus grande au monde.
    <br> Et toi et nous en faisons partie. Dans ce blog, découvre les articles sur les plus grandes légendes du football, mais également des stars du moment et des futurs grand joueur.</h3>

    <div class="grid md:grid-cols-3 ">

      <div class="m-2 flex flex-col rounded-3xl border border-solid border-white p-5 " v-for="(post,index) in posts" :key="index">
        <img class="max-w-full rounded-t-3xl rounded-tr-3xl" :src="post.fields.couverture.fields.file.url" alt="" >

        <nuxt-link class="text-white sm:mt-2.5" v-bind:to="post.fields.tag">
          <span>{{post.fields.titre}}</span>
        </nuxt-link>

        <p class="text-white" id="preview">{{post.fields.body}}</p>

        <nuxt-link class="text-white w-3/5 text-center self-center  border border-solid border-green-800  pt-3 pb-3 pr-12 pl-12 rounded-2xl bg-green-800" id="plus" v-bind:to="post.fields.tag">
          <span>Plus</span>
        </nuxt-link>



      </div>
<!--      <div class="z-0" id="ballon">-->
<!--        <img src="../assets/ballon.png" alt="ballon">-->
<!--        <img src="../assets/ballon.png" alt="ballon">-->
<!--        <img src="../assets/ballon.png" alt="ballon">-->
<!--        <img src="../assets/ballon.png" alt="ballon">-->
<!--        <img src="../assets/ballon.png" alt="ballon">-->
<!--      </div>-->

<!--      <img src="../assets/terrain_de_foot.jpg" alt="terrain" id="terrain" class="z-0">-->
  </div>

  </div>


</template>

<script>
import {createClient} from '../plugins/contentful.js'

const client=createClient()

export default {
  asyncData({env}){
    return client.getEntries({
      content_type:'post'
    }).then(entries => {
      return {posts: entries.items}
    }).catch(e => console.log(e))
  }
}
</script>

<style>
*{
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  z-index: 2;
}

#preview{
  display: -webkit-box;
  -webkit-line-clamp:3;
  line-height: 26px;
  margin: 20px 0;
  -webkit-box-orient: vertical;
  overflow: hidden;
  text-align: justify;
}

#plus:hover{
  animation: plusAnim 1.5s linear;
}

@keyframes plusAnim {
  50%{
    transform: scale(1.2);
  }

  100%{
    transform: scale(1);
  }

}


#ballon img{
  position: absolute;
  height: 40px;
  z-index: 0;
  /*animation: ballon1 60s linear infinite;*/

}

#terrain{
  position: absolute;
  height: 40px;
  animation: terrain1 60s infinite linear;
}


@keyframes  ballon1 {
  100% {
    transform: translate3d(0, 0, 1px) rotate(360deg);
  }

}

@keyframes terrain1 {


}



/*.background span {*/
/*  width: 20vmin;*/
/*  height: 20vmin;*/
/*  border-radius: 20vmin;*/
/*  backface-visibility: hidden;*/
/*  position: absolute;*/
/*  animation: move;*/
/*  animation-duration: 45s;*/
/*  animation-timing-function: linear;*/
/*  animation-iteration-count: infinite;*/
/*}*/


#ballon img:nth-child(0) {
  top: 76%;
  left: 34%;
  animation-duration: 32s;
  animation-delay: -32s;
  transform-origin: 1vw 9vh;

}
#ballon img:nth-child(1) {
  top: 16%;
  left: 8%;
  animation-duration: 15s;
  animation-delay: -19s;
  transform-origin: 9vw -18vh;

}
#ballon img:nth-child(2) {
  top: 41%;
  left: 66%;
  animation-duration: 51s;
  animation-delay: -23s;
  transform-origin: 9vw -21vh;

}
#ballon img:nth-child(3) {
  top: 51%;
  left: 72%;
  animation-duration: 28s;
  animation-delay: -42s;
  transform-origin: 19vw 23vh;

}
#ballon img:nth-child(4) {
  top: 70%;
  left: 48%;
  animation-duration: 13s;
  animation-delay: -2s;
  transform-origin: -19vw 23vh;

}
#ballon img:nth-child(5) {
  top: 95%;
  left: 27%;
  animation-duration: 40s;
  animation-delay: -34s;
  transform-origin: 4px 18px;
}


</style>
