<template>
<div class="album">
    <h1 id="tabloBaslik">
        <span v-if="!isTurkish"> Works</span>
        <span v-else>Çeviriler</span>
    </h1>
    <div class="card">
        <a href="https://www.hepsiburada.com/sagduyulu-yatirim-rehberi-emre-ergin-p-HBCV00000UHQYP" target="_blank">
            <img src="../assets/syr.jpg" alt="The Little Book of Common Sense Investing"/>
        </a>
    </div>
    <div class="card">
        <a href="https://rayfowler.itch.io/remnants-of-the-precursors" target="_blank">
            <img src="../assets/rop.jpg" alt="Remnants of The Precursors" class="genisImg"/>
        </a>
    </div>
    <div class="card">
        <a href="https://store.steampowered.com/app/498380/AquaNimble/" target="_blank">
            <img src="../assets/an.jpg" alt="AquaNimble"  class="genisImg"/>
        </a>
    </div>
    <div class="card">
        <a href="https://store.steampowered.com/app/342610/HyperRogue/" target="_blank">
            <img src="../assets/hr.png" alt="Hyper Rogue"  />
        </a>
    </div>
    <div class="card">
        <a href="https://store.steampowered.com/app/312280/Simply_Chess" target="_blank"> 
            <img src="../assets/sc.jpg" alt="Simply Chess"  class="genisImg"/>
        </a>
    </div>
    <div class="card">
        <a href="https://store.steampowered.com/app/368700/Mysterious_Space/" target="_blank">    
            <img src="../assets/ms.jpg" alt="Mysterious Space"  class="genisImg"/>
        </a>
    </div>

</div>

</template>

<script setup>
const props = defineProps(['isTurkish']);
</script>

<style>
a>.genisImg,.card>.genisImg{
    object-fit: contain;
    height: auto;
    width: 10vw;
    margin-top:4vh;
    margin-bottom:4vh;
}

@media (max-width:1000px) { 
    a>.genisImg,.card>.genisImg{
    object-fit: contain;
    height: auto;
    width: 30vw;
}
}

</style>