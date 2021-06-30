<template>

  <body>
    <header>
      <h1>Les bases de CSS</h1>
    </header>
    <main>
      <div class="positioning">
        <h2>Positioning</h2>
        <span>relative</span>
        <span id="circle">absolute</span>
        <span id="rectangle">absolute</span>
      </div>

      <div class="flexbox">
        <h2>Flexbox</h2>

        <ul>
          <li>
            <a href="https://flexbox.help/" >https://flexbox.help/</a>
          </li>

          <li>
            <a href="https://flexbox.help/">https://flexbox.help/</a>
          </li>

          <li>
            <a href="https://flexbox.help/">https://flexbox.help/</a>
          </li>

        </ul>
      </div>


      <div class="grid">
        <h2>Grid</h2>
        <div class="grid-container">
          <div class="img">
            <img src="../assets/logo_css.png" alt="logo" class="logo">
          </div>
          <form>
            <input type="text" id="firstname" placeholder="Prénom">
            <input type="text" id="surname" placeholder="Nom">
            <textarea cols="30" rows="30" placeholder="Ici votre message"></textarea>
            <input type="submit" value="Valider">
          </form>

        </div>
      </div>
    </main>
  </body>

</template>

<script>
import Index from "./index";
export default {
  name: "css",
  components: {Index}
}
</script>

<style scoped lang="css">
@import url('https://fonts.googleapis.com/css2?family=Playfair+Display:wght@500&display=swap');



.logo{
  height: 200px;
  margin: 0 auto;
}

h1{
  text-transform: uppercase;
  letter-spacing: 2px;
  font-size: 2.5rem;
  color: #c4c4ff;
  text-shadow: 4px 0px 0px rgba(45, 226, 226, 0.24);
  text-align: center;
  font-family: 'Playfair Display', serif;

}


body {
  position: absolute;
  font-family: 'Agency FB',sans-serif;
  background: moccasin;
  background: url("../assets/sunset.jpg") no-repeat fixed center/cover;
  width: 100%;
}



main{

  background: rgba(245, 245, 245, 0.93);
  width: 90%;
  min-height: 500px;
  margin: 10px auto;
  padding: 15px;
  border-radius: 15px;
  box-shadow: 0 2px 12px 5px rgba(0, 0, 0, 0.253);
}

.positioning,.flexbox, .grid{
  border: 2px solid skyblue;
  padding: 10px;
  margin-top: 20px;
  border-radius: 10px;

}


/************************* POSITIONING ************************/
.positioning{
  position: relative;
}

h2{
  margin: 0;
}

#circle {
  height: 60px;
  width: 60px;
  background: skyblue;
  padding: 20px;
  border-radius: 50%;
  position: absolute;
  top:-10px;
  right: 110px;
  box-shadow: 0 2px 12px 5px rgba(51,51,51,0.13);
  z-index: 1;
}

#rectangle {
  height: 15px;
  width: 150px;
  background: slateblue;
  padding: 20px;
  position: absolute;
  bottom: 2px;
  left: 50%;
  transform: translateX(-50%);
}



/************************* FLEXBOX ************************/
ul{
  display: flex;
  justify-content: space-around;
}


li{
  list-style-type: none;
  font-size: 0.7rem;
  height: 160px;
  width: 160px;
  background: turquoise;
  display: flex;
  align-items: center;
  justify-content: center;
}



/***********GRID******/

.grid-container{
  display: grid;
  grid-template-columns: 30% 70%;;
  padding: 20px;
}

form {
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-template-rows: 1fr 1fr 1fr;
  grid-template-areas:
    "i1 i2"
    "ta ta"
    "bt bt";
}

input,textarea{
  margin: 5px;
  height: 45px;
  border: 1px solid darkblue;
  padding: 10px;
  border-radius: 5px;
  font-size: 1.1rem;
}


#firstname {
  grid-area: i1;
}

#surname{
  grid-area: i2;
}

textarea{
  grid-area: ta;
  resize: none;
}

input[type="submit"]{
  grid-area: bt;
  cursor: pointer;
  background: cyan;
  transition: 1s;
}

input[type="submit"]:hover{
  background: darkblue;
  color: white;
}


/********** RESPONSIVE ***************/

@media screen and (max-width: 1000px){

  .grid-container{
    display: block;
  }


}


@media screen and (max-width: 700px){

  form {
    grid-template-columns: 1fr;
    grid-template-rows: 1fr 1fr 1fr 1fr;
    grid-template-areas:
    "i1"
    "i2"
    "ta"
    "bt";
  }


}
</style>
