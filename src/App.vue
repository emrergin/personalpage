<script setup>
import Author from "./components/Author.vue";
import Translator from "./components/Translator.vue";
import Developer from "./components/Developer.vue";
import Academic from "./components/Academic.vue";
import { ref , onMounted } from 'vue';
import { Icon } from '@vicons/utils';
import {Github,Twitter,GoodreadsG} from '@vicons/fa/';

const bakilan=ref(0);
const zaman1=ref(false);
const zaman2=ref(false);

onMounted(() => {
  setTimeout(() =>zaman1.value=true, 1000);
  setTimeout(() =>zaman2.value=true, 2500);
})


</script>

<template>
    <Transition name="solTaraf" >
      <Author v-if="bakilan===1" class="solTaraf2"/>
    </Transition>
    <Transition name="solTaraf" >
      <Translator v-if="bakilan===2" class="solTaraf2"/>
    </Transition>


<div id="general" :class="[
  {solBorder:(bakilan===1||bakilan===2)},
  {sagBorder:(bakilan===3||bakilan===4)},
  {noBorder: !bakilan}]">
  <div id="welcomeText">
    <h1 > Hello!</h1>
    <Transition name="solTaraf">
      <h2 class="gecis" v-if="zaman1">I am Emre.</h2>
    </Transition>
    <Transition name="sagTaraf">
      <h3 class="gecis" v-if="zaman2">I am many things.</h3>
    </Transition>      
  </div>
  <div id="mainContent">
    <div id="photoFrame">
        <img alt="Handsome man" src="./assets/handsome.jpg" />
    </div>
    <div id="drawer">
      <div class="drawerItem d1"  @mouseover="bakilan= 1" @click="bakilan= 1" :class="{ highLight: bakilan===1 }"> An Author </div>
      <div class="drawerItem d2"  @mouseover="bakilan= 2" @click="bakilan= 2" :class="{ highLight: bakilan===2 }"> A Translator</div>
      <div class="drawerItem d3"  @mouseover="bakilan= 3" @click="bakilan= 3" :class="{ highLight: bakilan===3 }"> A Web Developer</div>
      <div class="drawerItem d4"  @mouseover="bakilan= 4" @click="bakilan= 4" :class="{ highLight: bakilan===4 }"> An Academic</div>
    </div>
    <div id="mediaLinks">
      <a href="https://github.com/emrergin/" target="_blank">
        <Icon size="36">        
          <Github />
        </Icon>
      </a>
      <a href="https://twitter.com/zulmetefza" target="_blank">
        <Icon size="36">
            <Twitter />
        </Icon>
      </a>
      <a href="https://www.goodreads.com/author/show/9244242.Emre_Ergin" target="_blank">
        <Icon size="36">
          <GoodreadsG />
        </Icon>
      </a>
    </div>
</div>

</div>
<Transition name="sagTaraf" >
  <Developer v-if="bakilan===3" class="sagTaraf2"/>
</Transition>
<Transition name="sagTaraf" >
  <Academic v-if="bakilan===4" class="sagTaraf2"/>
</Transition>  
</template>



<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto+Slab&display=swap');
:root {
  --renk1: #b6f6ca;
  --renk2: #ddfbe0;
  --renk3: #9ef2d9;
  --renk4: black;
  --renk5: black;
}

body{
  margin:0px;  
  background-color: var(--renk3);
  height: 100vh;
  overflow: hidden;
}

#app {
  font-family: 'Roboto Slab', serif;
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
  height: 620px;
  font-size:16px;
  top: 30%;
  -ms-transform: translateY(-30%);
  transform: translateY(-30%);
  box-shadow: rgba(0, 0, 0, 0.3) 0px 19px 38px, rgba(0, 0, 0, 0.22) 0px 15px 12px;
}

#photoFrame{
  border: var(--renk1) solid 20px;
  border-radius: 50%;
  overflow: clip;
  height: 10vw;
  width: 10vw;  
  position: absolute;
  margin: auto; 
  left: 0; 
  right: 0; 
  top: 0;
  bottom: 200px;
  z-index: 10;
}

#photoFrame > img{
  height: 10vw;
  width: 10vw;
  object-fit: cover;
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
  transition: all 0.5s ease-in;
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
  height: 100px;
  padding-bottom: 200px;
  grid-template-areas: 
    "d1 . d3"
    "d2 . d4";
}

#mediaLinks{
  display:flex;
  gap: 10px;
  /* margin-bottom:50px; */
}

#mediaLinks>a{
  color:var(--renk4);
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
  padding: 15px;
  border: var(--renk2) solid 3px;
  border-radius: 5px;
  filter: brightness(90%)
}

.drawerItem.highLight, .drawerItem:hover{
   filter: brightness(100%)
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
  border-right: var(--renk2) solid 5px;
  border-left: var(--renk2) solid 5px;
}
.sagBorder{
  border-right: var(--renk1) solid 5px;
  border-left: var(--renk2) solid 5px;
}

.solBorder{
  border-left: var(--renk1) solid 5px;
  border-right: var(--renk2) solid 5px;
}

@media (max-width:700px) { 
  #app{
    position:static;
    -ms-transform: translateY(0%);
    transform: translateY(0%);
    border:0px;
    height: auto;
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
    place-items:start;
    place-content:start;
    box-shadow: rgba(0, 0, 0, 0.24) 0px 3px 8px;
  }

  #welcomeText{
    /* align-self:stretch; */
    position:absolute;
    top: 35vw;
    width:38vw;
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
    /* grid-template-columns:1fr 0.4fr 1fr ;
    grid-template-rows: 1fr 2fr 1fr ; */
    /* width: 100%; */
    justify-content: stretch;
    height: 100px;
    padding-bottom: 200px;
    /* grid-template-areas: 
      "d1 . d3"
      "d2 . d4"; */
  }

  .d1,.d2,.d3,.d4{
    text-align:center;
  }

  .drawerItem{
    background-color: var(--renk1);
    color: black;
    padding: 15px;
    border: var(--renk2) solid 3px;
    border-radius: 5px;
    filter: brightness(90%)
  }
  .drawerItem.highLight, .drawerItem:hover{
    filter: brightness(100%)
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

  #photoFrame{
    border: var(--renk1) solid 20px;
    border-radius: 50%;
    overflow: clip;
    height: 30vw;
    width: 30vw;  
    position: static;
    margin: auto; 
    left: 0; 
    right: 0; 
    top: 0;
    bottom: 200px;
    z-index: 10;
    margin-bottom: 35vw;
  }

  #photoFrame > img{
    height: 30vw;
    width: 30vw;
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
}
</style>
