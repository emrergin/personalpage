<script setup>
import Author from "./components/Author.vue";
import Translator from "./components/Translator.vue";
import Developer from "./components/Developer.vue";
import Academic from "./components/Academic.vue";
import { ref , onMounted } from 'vue';
import { Icon } from '@iconify/vue';
import emailEditOutline from '@iconify-icons/mdi/email-edit-outline';
import githubIcon from '@iconify-icons/mdi/github';
import goodreadsIcon from '@iconify-icons/mdi/goodreads';
import twitterIcon from '@iconify-icons/mdi/twitter';

const bakilan=ref(0);
const zaman1=ref(false);
const zaman2=ref(false);
// const idleT=ref(false);
const isTurkish=ref(false);

let icons={
				emailEditOutline,
        githubIcon,
        twitterIcon,
        goodreadsIcon
			};

onMounted(() => {
  setTimeout(() =>zaman1.value=true, 1000);
  setTimeout(() =>zaman2.value=true, 2500);
  let idleTimer = setInterval(() =>{
    if (bakilan.value===0){
      bakilan.value=Math.floor(Math.random() * 4) + 1;
    } else{
      bakilan.value++;
      bakilan.value=(bakilan.value-1)%4+1;
    }
  }
  , 5000);

  window.addEventListener("resize", textPlacer);
  if (window.innerWidth < 1000) {
    let metin=document.getElementById(`welcomeText`);
    document.getElementById(`photoFrame`).after(metin);
    // let appHeight=document.getElementById(`app`).offsetHeight+2.2*document.getElementById(`textIlkSatir`).offsetHeight;
    // document.getElementById(`app`).style.height=`${appHeight}px`;
  }
  if (navigator.language===`tr-TR`){
    isTurkish.value=true;
  }
})

function textPlacer(){
  if (window.innerWidth < 1000) {
    let metin=document.getElementById(`welcomeText`);
    document.getElementById(`photoFrame`).after(metin);
  }
  else{
    let metin=document.getElementById(`welcomeText`);
    document.getElementById(`mainContent`).before(metin);
  }
}
</script>

<template>
    <Transition name="solTaraf" >
      <Author v-if="bakilan===1" class="solTaraf2" :isTurkish="isTurkish"/>
    </Transition>
    <Transition name="solTaraf" >
      <Translator v-if="bakilan===2" class="solTaraf2" :isTurkish="isTurkish"/>
    </Transition>

<div id="general" :class="[
  {solBorder:(bakilan===1||bakilan===2)},
  {sagBorder:(bakilan===3||bakilan===4)},
  {noBorder: !bakilan}]">
  <div id="welcomeText">
    <h1 id="textIlkSatir"> 
      <span v-if="!isTurkish">Hello!</span>
      <span v-else>Selam!</span>
    </h1>
    <Transition name="solTaraf">
      <h2 class="gecis" v-if="zaman1">
        <span v-if="!isTurkish"> I am Emre.</span>
        <span v-else>Ben Emre.</span>
      </h2>
    </Transition>
    <Transition name="sagTaraf">
      <h3 class="gecis" v-if="zaman2">
        <span v-if="!isTurkish">I am many things.</span>
        <span class="kucukYazi2" v-else>Aşağıdakilerin hepsiyim.</span>
      </h3>
    </Transition>      
  </div>
  <div id="mainContent">
    <div id="photoFrame">
        <img alt="My Face" src="./assets/proPic.png" />
    </div>
    <div id="drawer">
      <div class="drawerItem d1"  @mouseover="bakilan= 1" @click="bakilan= 1;clearInterval(idleTimer);" 
          :class="{ highLight: bakilan===1 }"> 
        <span v-if="!isTurkish">An Author</span> 
        <span v-else>Yazar</span>
      </div>
      <div class="drawerItem d2"  @mouseover="bakilan= 2" @click="bakilan= 2;clearInterval(idleTimer);" 
          :class="{ highLight: bakilan===2 }"> 
        <span v-if="!isTurkish">A Translator</span>
        <span v-else>Çevirmen</span>
      </div>
      <div class="drawerItem d3"  @mouseover="bakilan= 3" @click="bakilan= 3;clearInterval(idleTimer);" 
          :class="{ highLight: bakilan===3 }"> 
        <span v-if="!isTurkish">A Web Developer</span>
        <span v-else>Web Geliştiricisi</span>
      </div>
      <div class="drawerItem d4"  @mouseover="bakilan= 4" @click="bakilan= 4;clearInterval(idleTimer);" 
          :class="{ highLight: bakilan===4 }"> 
        <span v-if="!isTurkish">An Academic</span>
        <span v-else class="kucukYazi2">Akademisyen</span>
      </div>
    </div>
    <div id="mediaLinks">
      <a href="mailto: emrergin2757@yahoo.com" target="_blank">
        <Icon :icon="icons.emailEditOutline"  id="icon1" align="center,slice" verticalAlign="center,slice"/>        
      </a>
      <a href="https://github.com/emrergin/" target="_blank">
        <Icon :icon="icons.githubIcon"   id="icon2" align="center,slice" verticalAlign="center,slice"/>
      </a>
      <a href="https://twitter.com/zulmetefza" target="_blank">
        <Icon :icon="icons.twitterIcon"  id="icon3" align="center,slice" verticalAlign="center,slice"/>
      </a>
      <a href="https://www.goodreads.com/author/show/9244242.Emre_Ergin" target="_blank">
        <Icon :icon="icons.goodreadsIcon"   id="icon4" align="center,slice" verticalAlign="center,slice" />
      </a>
    </div>
</div>

</div>
<Transition name="sagTaraf" >
  <Developer v-if="bakilan===3" class="sagTaraf2" :isTurkish="isTurkish"/>
</Transition>
<Transition name="sagTaraf" >
  <Academic v-if="bakilan===4" class="sagTaraf2" :isTurkish="isTurkish"/>
</Transition>  
</template>



<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins&display=swap');

:root {
  --renk1: #00B4FF;
  --renk2: #EEEEEE;
  --renk3: #515151;
  --renk4: #041122;
  --renk5: #041122;
}

body{
  margin:0px;  
  background-color: var(--renk3);
  height: 100vh;
  overflow-y: auto;
  overflow-x: hidden;
  display: flex;
  flex-direction:column;
}

#app {
  font-family: 'Poppins', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  display: grid;
  background-color: var(--renk2);
  margin: 0px;
  padding: 0px;
  grid-gap: 0px;
  color: var(--renk4);
  place-items: center;
  place-content:center;
  grid-template-columns:30% 35% 30% ;
  grid-template-rows: 1fr;
  position:relative;
  justify-items: stretch;
  /* height: 620px; */
  font-size:1.5vh;
  top: 30%;
  -ms-transform: translateY(-30%);
  transform: translateY(-30%);
  box-shadow: rgba(0, 0, 0, 0.3) 0px calc(15px + 0.4vw) calc(30px + 0.8vw), rgba(0, 0, 0, 0.22) 0px calc(11px + 0.4vw) calc(8px + 0.4vw);
  width: 100vw;
  align-self: center;
}

#general{
  display:flex;
  flex-direction: column;
  justify-content: space-around;
  height:100%;
  grid-column-start: 2;
  grid-column-end: 3;
  padding:0px;
  margin:0px;
  transition: transform 0.5s ease-in;
  transition: opacity 0.5s ease-in;
}

#mainContent{
  position: relative;
  display:flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

#drawer{
  display:grid;
  grid-template-columns:1fr 0.4fr 1fr ;
  grid-template-rows: 1fr 2fr 1fr ;
  width: 100%;
  justify-content: stretch;
  height: 5vw;
  /* padding-bottom: 200px; */
  grid-template-areas: 
    "d1 . d3"
    "d2 . d4";
}

#photoFrame{
  border: var(--renk1) solid 1.5vh;
  border-radius: 50%;
  overflow: clip;
  height: min(10vw,30vh);
  width: min(10vw,30vh); 
  position: absolute;
  margin: auto; 
  left: 0; 
  right: 0; 
  top: calc(-1/3 * min(10vw,30vh));
  /* bottom: auto; */
  z-index: 10;
}

#photoFrame > img{
  height: min(10vw,30vh);
  width: min(10vw,30vh); 
  object-fit: cover;
}

.d1,.d2{
  text-align:left;
}

.d3,.d4{
  text-align:right;
}

.drawerItem{
  background-color: var(--renk1);
  color: var(--renk5);
  padding: 1.5vh;
  border: var(--renk2) solid 3px;
  border-radius: 0.75vh;
  filter: brightness(90%);
}

.drawerItem.highLight, .drawerItem:hover{
   filter: brightness(100%);
}

.d1{
  grid-area: d1;
}
.d2{
  grid-area: d2;
}
.d3{
  grid-area: d3;
}
.d4{
  grid-area: d4;
}

#mediaLinks{
  display:flex;
  gap: 1vh;
  justify-content: center;
  align-items:center;
}

#mediaLinks>a{
  color:var(--renk4);
  display: flex;
  justify-content: stretch;
  align-items:stretch;
}

#mediaLinks>a:hover{
  color:var(--renk1);
  transform: scale(1.1);
  transition:all 0.5s ease-in;
}


svg,path{
  height:100%;
  width:100;
}

#icon1{
  height:3.4vh;
  width:3vh;
}

#icon2{
  height:3.4vh;
  width:2.8vh;
}
#icon3{
  height:3.4vh;
  width:2.6vh;
}

#icon4{
  height:3.4vh;
  width:1.75vh;
}


.solTaraf-enter-active,
.sagTaraf-enter-active{
 transition: all 0.6s ease;
}

.solTaraf-enter-from,
.solTaraf-leave-to {
  opacity: 0;
  transform: translateX(-40%) ;
  position: absolute;
}

.sagTaraf-enter-from,
.sagTaraf-leave-to {
  opacity: 0;
  transform: translateX(40%);
  position: absolute;
}

.noBorder{
  border-right: var(--renk2) solid 0.5vw;
  border-left: var(--renk2) solid 0.5vw;
}
.sagBorder{
  border-right: var(--renk1) solid 0.5vw;
  border-left: var(--renk2) solid 0.5vw;
}

.solBorder{
  border-left: var(--renk1) solid 0.5vw;
  border-right: var(--renk2) solid 0.5vw;
}

@media (min-width:1001px){
  #app{
  height: 33vw;
  }
  #mainContent{
    margin-top:5vh;
    height:60%;
    justify-content:space-between;
  }
  
}

@media (max-width:1000px) { 
  #app{
    position:static;
    -ms-transform: translateY(0%);
    transform: translateY(0%);
    border:0px;
    height: 620px;
    grid-template-columns:3fr 7fr ;
    grid-template-rows: 1fr;
    position:relative;
    width:100vw;
  }

  .noBorder,.sagBorder,.solBorder{
    border:0px;
  }

  #general{
    grid-column-start: 1;
    grid-column-end: 2;
    grid-row-start: 1;
    grid-row-end: 2;
    display:flex;
    justify-content:flex-start;
    align-items: center;
    box-shadow: rgba(0, 0, 0, 0.24) 0px 3px 8px;
    width:33vw;
    height:100%;
  }

  #mainContent{
    width:100%;
    height:100%;
  }


  #emailButton{
    order:99;
  }

  .solTaraf2,.sagTaraf2{
    grid-column-start: 2;
    grid-column-end: 3;
    grid-row-start: 1;
    grid-row-end: 2;
  }
  body{
    overflow-y: auto ;
    display:flex;
    flex-direction: column;
    height: auto;
    width:100vw;
  }
  #drawer{
    display:flex;
    flex-direction:column;
    justify-content: stretch;
    height: 200px;
  }

  #mediaLinks{
    margin-top:auto;
    width:100%;
    justify-self:flex-end;
  }

  .d1,.d2,.d3,.d4{
    text-align:center;
  }

  #mediaLinks>a{
    width:20%;
    display:flex;
    justify-content:center;
  }

  #photoFrame{
    border: var(--renk1) solid 15px;
    border-radius: 50%;
    overflow: clip;
    height: calc(33vw - 30px);
    width: calc(33vw - 30px);  
    position: static;
    margin: auto; 
    z-index: 10;
    box-shadow: 0px min(1vw,5px) min(1vw,5px);
  }

  #photoFrame > img{
    height: calc(33vw - 30px);
    width: calc(33vw - 30px);  
    object-fit: cover;
  }

  .solTaraf-enter-from,
  .solTaraf-leave-to ,
  .sagTaraf-enter-from,
  .sagTaraf-leave-to {
    opacity: 0;
    transform: translateX(40%);
    position: absolute;
  }

  .kucukYazi2{
    font-size:0.85em;
  }
}
</style>
