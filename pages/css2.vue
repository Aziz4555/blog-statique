<template>
      <body>
        <div class="card">
          <h1>CSS Partie 2</h1>

          <div class="grid-container">
            <div class="polyon-container">
              <div class="polygon"></div>
            </div>
            <p>
              Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum
            </p>
          </div>

          <div class="checkbox-container">
            <input type="checkbox" id="option1">
            <label for="option1">Option 1</label>

            <input type="checkbox" id="option2">
            <label for="option2">Option 2</label>

            <input type="checkbox" id="option3">
            <label for="option3">Option 3</label>

          </div>
          <div class="email">
            <input type="text" placeholder="Entrez votre email">
          </div>

          <button type="submit">Valider</button>
          <a href="https://www.google.com">condition générale de vente</a>
        </div>

      <img src="../assets/spaceship.png" alt="spaceship">

      </body>
</template>

<script>
export default {
  name: "css2"
}
</script>

<style scoped >


:root{
  --color1:#ede4d0;
  --color2:pink;
  --color3:#393b4b;
  --color4:rgb(18,19,19)
}

*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}



body{
  background: url("../assets/voix_lacte.jpg") no-repeat center/cover;
  height: 100vh;
  font-family: "Segoe UI",Verdana,Tahoma,sans-serif;
  color: #ede4d0;
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
}

.card{
  background: rgba(0, 0, 0, 0.49);
  width: calc(100% - 50px);
  padding: 20px 20px 6px;
  box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.47);
  border-radius: 5px;
  backdrop-filter: blur(20px);
  z-index: 1;
}


.card:before{
  content: "\2730";
  position: absolute;
  top:14px;
  right: 20px;
  font-size: 3rem;
}


h1{
  font-size: 3rem;
  margin-bottom: 24px;
  position: relative;
}

h1:after{
  content: "";
  position: absolute;
  background: pink;
  height: 1px;
  width: 100%;
  bottom: -14px;
  left: 50%;
  transform: translateX(-50%) scaleX(0);
  animation: h1anim 6s ease-in-out forwards;
  transform-origin: center;
}

@keyframes h1anim {
  to{
    transform: translateX(-50%) scaleX(1);
  }
}


.grid-container{
  display: grid;
  grid-template-columns: 20% 80%;
}


.polyon-container{
  filter: drop-shadow(-1px 6px 3px pink);
  /* Mettre le parent en grid */
  place-self: center left;
}

.polygon{
  clip-path: polygon(50% 0%, 100% 50%, 50% 100%, 0% 50%);
  background: linear-gradient(135deg, #ede4d0 0%, pink 100%);
  height: 100px;
  width: 100px;
  box-shadow: 2px 2px 2px 4px yellow;
}

.polygon:after{
  content: "Un texte";
  position: absolute;
  color: pink;
  background: rgb(18,19,19);
  top: 50%;
  left: 50%;
  transform: translate(-50%,-50%) rotate(344deg);
  width: 90px;
  padding: 4px;
  text-align: center;
}

p {
  line-height: 26px;
  margin: 20px 0;
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-line-clamp:4;
  overflow: hidden;
  text-align: justify;
}

p::selection{
  background: pink;
  color: #393b4b;
}

.checkbox-container {
  display: flex;
  justify-content: space-around;
  margin: 20px 0 30px;
  perspective: 40px;
}
input[type="checkbox"] {
  display: none;
}

input[type="checkbox"]:checked + label {
  background: pink;
  color: #393b4b;
  transform: scale(1.1);
  filter: brightness(110%);
}

label{
  cursor: pointer;
  border: 1px solid #ede4d0 ;
  background: #393b4b;
  padding: 10px;
  border-radius: 5px;
  transition: 0.2s;
  user-select: none;
}


label:first-of-type:hover{
  animation: label1 1s infinite linear;
}

@keyframes label1 {
  50%{
    transform: scale(1.2);
  }

  100%{
    transform: scale(1);
  }
}

label:nth-child(4):hover {
  animation: label2 3s infinite linear;
}

/* Ne pas oublier la perspective sur le parent */
@keyframes label2 {
  33% {
    transform: translateZ(30px);
  }

  66%{
    transform: translateZ(-40px);
  }

  100%{
    transform: translateZ(0);
  }

}

.email{
  text-align: center;
  margin-bottom: 20px;
}

.email input{
  padding: 10px;
  border-radius: 5px;
  outline: none;
  border:3px solid transparent;
  text-align: center;
  font-size: 1.1rem;
  color: #ede4d0;
  width: 35%;
  max-width: 300px;
  min-width: 180px;
  transition: 0.3s;
}

input[type="text"]:focus{
  background: transparent;
  border:3px solid pink;
  border-radius: 150px;
}


input[type="placeholder"]::placeholder{
  color: pink;
  font-family: "Gill Sans MT",sans-serif;
}

button {
  cursor: pointer;
  background: pink;
  border: none;
  font-size: 1.3rem;
  padding: 10px 20px;
  border-radius: 150px;
  margin: 0 auto;
  display: block;
  color: #393b4b;
  transition: 1s;
  outline: none;
}

button:hover{
  letter-spacing: 3px;

}

button:active {
  transform: scale(1.2);

}

button:hover + a,
a:hover{
  opacity: 1;
  transform: translateY(0);
  visibility: visible;

}

a{
  opacity: 0;
  display: block;
  visibility: hidden;
  color: pink;
  text-align: center;
  transform: translateY(20px);
  transition: 0.5s;
}


a:visited{
  color: pink;
}

img {
  height: 40px;
  position: absolute;
  filter: drop-shadow(0 6px 3px rgba(255,255,0,0.6));

  animation: spaceship 60s infinite linear;
}

@keyframes spaceship {
  0%{
    top:14%;
    left: 2%;
    transform: rotate(95deg);
  }

  20%{
    top:18%;
    left: 60%;
    transform: rotate(60deg);
  }

  30%{
    top:20%;
    left: 80%;
    transform: rotate(90deg);
  }

  40%{
    top:15%;
    left: 120%;
    transform: rotate(110deg);
  }

  50%{
    top:50%;
    left: 80%;
    transform: rotate(323deg);
  }

  60%{
    top:90%;
    left: 90%;
    transform: rotate(256deg);
  }

  70%{
    top:110%;
    left: 50%;
    transform: rotate(237deg);
  }

  80%{
    top:85%;
    left: 30%;
    transform: rotate(323deg);
  }

  90%{
    top:50%;
    left: 15%;
    transform: rotate(350deg);
  }

  100%{
    top:14%;
    left: 2%;
    transform: rotate(95deg);
  }
}

</style>
