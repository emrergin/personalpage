<template>
<div class="album">
    <h1 id="tabloBaslik1">
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

<h1 id="tabloBaslik2" class="kucukYazi">
    <span v-if="!isTurkish"> Affiliations</span>
    <span v-else>Akademik Geçmişim</span>  
</h1>
<a href="http://www.ibu.edu.tr/en" 
    target="_blank"
    class="drawerItem article"
>	
Bolu Abant İzzet Baysal <span v-if="!isTurkish"> University</span><span v-else>Üniversitesi</span>      
</a>
<a href="https://www.maastrichtuniversity.nl/" 
    target="_blank"
    class="drawerItem article">
Maastricht <span v-if="!isTurkish"> University</span><span v-else>Üniversitesi</span>
</a>  
<a href="https://www.uni-corvinus.hu/?lang=en/" 
    target="_blank"
    class="drawerItem article">
Corvinus <span v-if="!isTurkish"> University</span><span v-else>Üniversitesi</span>
</a>  
<a href="https://w3.bilkent.edu.tr/bilkent/" 
    target="_blank"
    class="drawerItem article">
Bilkent <span v-if="!isTurkish"> University</span><span v-else>Üniversitesi</span> 
</a>  
<a href="https://www.etu.edu.tr/en/" 
    target="_blank"
    class="drawerItem article">
TOBB ETÜ <span v-if="!isTurkish"> University</span><span v-else>Üniversitesi</span>
</a>  

</div>
</template>

<script setup>
const props = defineProps(['isTurkish']);
</script>

<style>
.article{
grid-column: span 2;
}

.kucukYazi{
    transform: scale(0.9);
}

.album>.drawerItem{
    align-self:stretch;
}
</style>

