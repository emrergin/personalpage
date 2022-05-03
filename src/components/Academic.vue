<template>
<div class="album2">
    <h1 >
        <span v-if="!isTurkish"> Articles</span>
        <span v-else>Makaleler</span>
    </h1>

<a href="https://link.springer.com/content/pdf/10.1007/s00199-020-01312-x.pdf" 
    target="_blank"
    class="drawerItem article">
    <span v-if="!isTurkish"> How to choose a fair delegation?</span>
    <span v-else>Adil bir delegasyon nasıl seçilir?</span>
</a>
<a href="https://dergipark.org.tr/en/download/article-file/2117669" 
    target="_blank"
    class="drawerItem article">
    <span v-if="!isTurkish"> The collective sectoral multipliers of the European Union</span>
    <span v-else>Avrupa Birliği'nin Kolektif Sektörel Çarpanları</span>
</a>    

<h1  class="kucukYazi">
    <span v-if="!isTurkish"> Current and Past Affiliations</span>
    <span v-else>Akademik Geçmişim</span>  
</h1>
<a href="http://www.ibu.edu.tr/en" 
    target="_blank"
    class="drawerItem article"
>	
Bolu Abant İzzet Baysal&nbsp;<span v-if="!isTurkish">University</span><span v-else>Üniversitesi</span>      
</a>
<a href="https://www.maastrichtuniversity.nl/" 
    target="_blank"
    class="drawerItem article">
Maastricht&nbsp;<span v-if="!isTurkish">University</span><span v-else>Üniversitesi</span>
</a>  
<a href="https://www.uni-corvinus.hu/?lang=en/" 
    target="_blank"
    class="drawerItem article">
Corvinus&nbsp;<span v-if="!isTurkish">University</span><span v-else>Üniversitesi</span>
</a>  
<a href="https://w3.bilkent.edu.tr/bilkent/" 
    target="_blank"
    class="drawerItem article">
Bilkent&nbsp;<span v-if="!isTurkish">University</span><span v-else>Üniversitesi</span> 
</a>  
<a href="https://www.etu.edu.tr/en/" 
    target="_blank"
    class="drawerItem article">
TOBB ETÜ&nbsp;<span v-if="!isTurkish">University</span><span v-else>Üniversitesi</span>
</a>  

</div>
</template>

<script setup>
const props = defineProps(['isTurkish']);
</script>

<style>
.album2{
    display:grid;
    grid-template-columns:1fr;
    grid-template-rows: 1fr 1.5fr 1.5fr 1fr 1.5fr 1.5fr 1.5fr 1.5fr 1.5fr;
    height:100%;
    overflow: auto;
    align-items: center;
}
.article{
    display: flex;
    align-items: center;
    justify-content: center;
}
.kucukYazi{
    transform: scale(0.9);
}
.album2>.drawerItem{
    align-self:stretch;
}

@media (max-width:1000px) { 

    .album2{
        grid-template-rows: auto;
        height:auto;
    }
}
</style>

