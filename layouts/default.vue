<template>
  <div>

    <nav class="flex items-center bg-green-700 p-3 flex-wrap ">
      <nuxt-link to="#" class="p-2 mr-4 inline-flex items-center">
        <span class="text-xl text-white font-bold uppercase tracking-wide">Blog</span>
      </nuxt-link>

        <button @click.prevent="toggle" class="text-white inline-flex p-3 hover:bg-green-800 rounded lg:hidden ml-auto"
                 id="burger">
          <i class="material-icons">menu</i>
        </button>

      <div class="top-nav w-full lg:inline-flex lg:flex-grow lg:w-auto hidden " id="navigation">

        <div class="lg:inline-flex lg:flex-row lg:ml-auto flex flex-col" id="menu">

            <nuxt-link v-on:click.native="Auclick('#Accueil')" class="lg:inline-flex lg:w-auto px-3 py-2 rounded text-gray-300 hover:text-white
            hover:bg-green-800" id="Accueil" to="/">
              <span>Accueil</span>
            </nuxt-link>

<!--          <nuxt-link @click.native="Auclick('#Articles')" class="lg:inline-flex lg:w-auto px-3 py-2 rounded text-gray-300 hover:text-white-->
<!--            hover:bg-green-800" id="Articles" to="/articles">-->
<!--            <span>Articles</span>-->
<!--          </nuxt-link>-->

            <nuxt-link @click.native="Auclick('#Auteur')" class="lg:inline-flex lg:w-auto px-3 py-2 rounded text-gray-300 hover:text-white
            hover:bg-green-800" id="Auteur" to="/auteur">
              <span>Auteur</span>
            </nuxt-link>

          <nuxt-link @click.native="Auclick('#CSS')" class="lg:inline-flex lg:w-auto px-3 py-2 rounded text-gray-300 hover:text-white
            hover:bg-green-800" id="CSS" to="/css">
            <span>CSS</span>
          </nuxt-link>

          <nuxt-link @click.native="Auclick('#CSS2')" class="lg:inline-flex lg:w-auto px-3 py-2 rounded text-gray-300 hover:text-white
            hover:bg-green-800" id="CSS2" to="/css2">
            <span>CSS2</span>
          </nuxt-link>

        </div>
      </div>

    </nav>

      <Nuxt />

  </div>
</template>

<style scoped>

#navigation{
  transition: 10s;
}

</style>

<script>
export default {
  methods:{
    toggle(){
      const  navigation =document.querySelector('#navigation')
      // navigation.animate([
      //   // {heigth:'toggle'}
      //   {margin:'0 0 0 0', width:'100%'},
      //   {margin:'35px 0 0 0', width:'100%'},
      //
      //
      // ], {
      //   duration:500,
      //   easing:'linear'
      // })
      navigation.classList.toggle('hidden')


      },

      Auclick(param){
        const  navigation =document.querySelector('#navigation')
        const menulink=document.querySelector(param)
        menulink.addEventListener('click', function (){
          navigation.classList.add('hidden')

        })
        // menulink.onclick=function (){
        //   navigation.classList.add('hidden')
        // }
      }
    }
  }

</script>


