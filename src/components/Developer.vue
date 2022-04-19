<template>
<div class="album">
    <h1 id="tabloBaslik">Sites</h1>
    <div class="card2">
        <img src="../assets/pru.png" alt="Risk Testing"/>
        <div class="cardText">
            Public repo is incoming...
        </div>
    </div>
    <div class="card2">
        <img src="../assets/atolye.png" alt="Ateliler"/>
        <div class="cardText">
            <a href="https://atolye.herokuapp.com/"
            target="_blank"
            >
                Live
            </a>
            <a href="https://github.com/emrergin/atolye"
            target="_blank"
            >
                Repo
            </a> 
        </div>
    </div>
    <div class="card2">
        <img src="../assets/czk.png" alt="Sketch"/>
        <div class="cardText">
            <a href="https://emrergin.github.io/etch-a-sketch/"
            target="_blank"
            >
                Live
            </a>
            <a href="https://github.com/emrergin/etch-a-sketch"
            target="_blank"
            >
                Repo
            </a> 
        </div>
    </div>
    <div class="card2">
        <img src="../assets/hsb.png" alt="Calc"/>
        <div class="cardText">
            <a href="https://emrergin.github.io/hasib"
            target="_blank"
            >
                Live
            </a>
            <a href="https://github.com/emrergin/hasib"
            target="_blank"
            >
                Repo
            </a> 
        </div>
    </div>

</div>

</template>

<style>
.card2{
    position: relative;
}

.card2>img{
    object-fit: contain;
    height: 250px;
    width: 10vw;
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
    font-size:20px;
    text-shadow: 2px 2px 4px var(--renk4), 0px 0px 14px var(--renk5);
    display:flex;
    flex-direction: column;
    gap: 10px;
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

@media (max-width:700px) { 
.card2>img{
    object-fit: contain;
    height: 150px;
    width: 20vw;
}


}
</style>
