<template>
<div class="album">
    <h1 id="tabloBaslik">        
        <span v-if="!isTurkish"> Sites</span>
        <span v-else>Websiteleri</span>
    </h1>
    <div class="card2">
        <img src="../assets/pru.png" alt="Risk Testing"/>
        <div class="cardText kucukYazi2">            
            <span v-if="!isTurkish"> Public repo is incoming...</span>
            <span v-else>Yapım aşamasında...</span>
        </div>
    </div>
    <div class="card2">
        <img src="../assets/atolye.png" alt="Literature Workshop"/>
        <div class="cardText">
            <a href="https://atolye.herokuapp.com/"
            target="_blank"
            >
                <span v-if="!isTurkish"> Live</span>
                <span v-else> Link</span>
            </a>
            <a href="https://github.com/emrergin/atolye"
            target="_blank"
            >
                <span v-if="!isTurkish"> Repo</span>
                <span v-else> Kodlar</span>
            </a>
        </div>
    </div>
        <div class="card2">
        <img src="../assets/soc.jpg" alt="Voting rules"/>
        <div class="cardText">
            <a href="https://emrergin.github.io/socialchoice/"
            target="_blank"
            >
                <span v-if="!isTurkish"> Live</span>
                <span v-else> Link</span>
            </a>
            <a href="https://github.com/emrergin/socialchoice"
            target="_blank"
            >
                <span v-if="!isTurkish"> Repo</span>
                <span v-else> Kodlar</span>
            </a>
        </div>
    </div>
    <div class="card2">
        <img src="../assets/czk.png" alt="Etch a Sketch"/>
        <div class="cardText">
            <a href="https://emrergin.github.io/etch-a-sketch/"
            target="_blank"
            >
                <span v-if="!isTurkish"> Live</span>
                <span v-else> Link</span>
            </a>
            <a href="https://github.com/emrergin/etch-a-sketch"
            target="_blank"
            >
                <span v-if="!isTurkish"> Repo</span>
                <span v-else> Kodlar</span>
            </a>
        </div>
    </div>
    <div class="card2">
        <img src="../assets/hsb.png" alt="Calculator"/>
        <div class="cardText">
            <a href="https://emrergin.github.io/hasib"
            target="_blank"
            >
                <span v-if="!isTurkish"> Live</span>
                <span v-else> Link</span>
            </a>
            <a href="https://github.com/emrergin/hasib"
            target="_blank"
            >
                <span v-if="!isTurkish"> Repo</span>
                <span v-else> Kodlar</span>
            </a>
        </div>
    </div>

</div>

</template>
<script setup>
const props = defineProps(['isTurkish']);
</script>

<style>
.card2{
    position: relative;
    margin-top:2vh;    
}

.card2>img{
    object-fit: cover;
    height: 10vw;
    width: 10vw;
    box-shadow: rgba(6, 24, 44, 0.4) 0px 0px 0px 2px, rgba(6, 24, 44, 0.65) 0px 4px 6px -1px, rgba(255, 255, 255, 0.08) 0px 1px 0px inset;
}
.card2:hover>img{
    filter:brightness(0.8) blur(2px) saturate(0.1);
}

.cardText{
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%) scale(0.01);
    transition: all 0.5s ease-in;
    font-size:1.75vmin;
    text-shadow: 0.2vmin 0.2vmin 0.4vmin var(--renk4), 0px 0px 1.4vmin var(--renk5);
    display:flex;
    flex-direction: column;
    gap: 2vmin;
    font-weight: bold;
    filter:saturate(3);
    color:var(--renk1);
}

.cardText>a{
    color:var(--renk1);
}

.card2:hover> .cardText{
    transform: translate(-50%, -50%) scale(1);
}

@media (max-width:1000px) { 
.card2>img{
    object-fit: contain;
    height: 30vw;
    width: 30vw;
}

.card2{
    margin-top:5vh;
}


.card2:hover> .cardText{
    max-width: 15vw;
}

}
</style>

