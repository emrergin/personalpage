<template>
<div class="album">
    <h1 id="tabloBaslik">        
        <span v-if="!isTurkish">Books</span>
        <span v-else>Kitaplar</span>
    </h1>
    <div class="card">
        <a href="https://www.iz.com.tr/dorduncu-dilek" target="_blank">
            <img src="../assets/dd.jpg" alt="Dorduncu Dilek"/>
        </a>
    </div>
    <div class="card">
        <a href="https://www.iz.com.tr/acziyetin-teknigi" target="_blank">
            <img src="../assets/at.jpg" alt="Acziyetin Tekniği"/>
        </a>        
    </div>
    <div class="card">
        <a href="https://www.iz.com.tr/bes-kere-halil" target="_blank">
            <img src="../assets/bhh.jpg" alt="Beş Kere Halil"/>
        </a>
    </div>
    <div class="card">
        <a href="https://www.ketebe.com/ruh-dememi-bagislayin" target="_blank">
            <img src="../assets/rdb.png" alt="Ruh Dememi Bağışlayın"/>
        </a>        
    </div>
    <h1 id="tabloBaslik2">        
        <span v-if="!isTurkish"> Collaborations</span>
        <span v-else>Seçkiler</span>
    </h1>
    <div class="card">
        <a href="https://www.ketebe.com/korkut-ata-ne-soyledi-aykut-ertugrul-guray-sungu" target="_blank">
            <img src="../assets/kans.png" alt="Korkut Ata Ne Söyledi"/>
        </a>        
    </div>
    <div class="card">
        <a href="https://www.ketebe.com/ac%C3%A2ibul-mahl%C3%BBk%C3%A2t" target="_blank">
            <img src="../assets/am.png" alt="Acaibül Mahlukat"/>
        </a>        
    </div>
    <div class="card">
        <a href="https://www.ketebe.com/seyyahlar-ve-kasifler-kitabi" target="_blank">
            <img src="../assets/skk.png" alt="Seyyahlar ve Kaşifler"/>
        </a>        
    </div>
</div>

</template>

<script setup>
const props = defineProps(['isTurkish']);
</script>

<style>
.album{
    display:grid;
    grid-template-columns:1fr 1fr  ;
    grid-template-rows: 1fr 2.5fr 2.5fr;
    height:100%;
    overflow: auto;
    align-items: center;
}


a>img,.card>img{
    object-fit: contain;
    height: auto;
    width: 10vw;
}

#tabloBaslik1, #tabloBaslik{
    grid-column-start: 1;
    grid-column-end: 3;
    grid-row-start:1;
    grid-row-end:2;
}

#tabloBaslik2{
    grid-column-start: 1;
    grid-column-end: 3;
    grid-row-start:4;
    grid-row-end:5;
}

a{
    display: block;
}
@media (max-width:1000px) { 

    a>img,.card>img{
        object-fit: contain;
        height: 150px;
        width: 30vw;
    }

    .album{
        grid-template-rows: auto;
        height:100%;
    }
}
</style>