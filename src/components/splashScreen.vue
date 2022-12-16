<script>
export default {
    data() {
        return{
            paleteIndex: 0,
            paleteColors: [['#f94144', '#F9C74F', '#277DA1', '#F5F5F5'], ['#00D1FF', '#FF007A', '#FFE600', '#F5F5F5'], ['#3A3238', '#664375', '#D282A6', '#E8B4BC'], ['#250902', '#38040E', '#800E13', '#AD2831']],
            paleteColorName:['colorful','punchy','soft','blood']
        }
    },
    methods:{
            paleteIndexAdd(){
                this.paleteIndex == 3 ? this.paleteIndex = this.paleteIndex-3 : this.paleteIndex++                   
            },
            paleteIndexSub(){
                this.paleteIndex == 0 ? this.paleteIndex = this.paleteIndex+3  : this.paleteIndex--
            }
    }
}
</script>

<template>
    <div class="splash-container">
        <div class="logo-animation">
            <div class=" letter a" :class="paleteColorName[paleteIndex]">df</div>
            <div class="letter b" :class="paleteColorName[paleteIndex]">df</div>
            <div class="letter c" :class="paleteColorName[paleteIndex]">df</div>
            <div class="letter d" :class="paleteColorName[paleteIndex]">df</div>

            <div class="palete-selector-container">
                <h4 @click="paleteIndexSub" class="palete-controler palete-prev" >{{'<'}}</h4>
                <template v-for="color in paleteColors[paleteIndex]" class="palete-selector">
                    <div :style="{backgroundColor:color}" class="palete-color"></div>
                </template>
                <h4 @click="paleteIndexAdd" class="palete-controler palete-next" >{{'>'}}</h4>
            </div>

        </div>
        <div class="text-animation">
            <h4 class="text">
                Show what you want, how you want.
                <p><span>"dfolio" by Derek Alvarado</span></p>
            </h4>
        </div>
    </div>
    <!-- <div @click="playAnimation">Play</div> -->
</template>

<style>
.palete-selector-container{
    display: flex;
    align-items: center;
    position:absolute;
    bottom: 10vh;
    z-index: 5;
}
.palete-color{
    width: 1rem;
    height: 1rem;
    transition: .2s ease-out;
}
.palete-controler{
    margin: .5rem;
    user-select: none;
    transition: .2s ease-out;
}
.palete-next:hover{
    transform: translateX(.5rem);
}
.palete-prev:hover{
    transform: translateX(-.5rem);
}
.splash-container {
    position: relative;
    display: flex;
    align-items: center;
    justify-content: center;
}
.text {
    text-align: left;
}
.text-animation {
    opacity: 0;
    animation: text-animation .3s ease-out .7s forwards;
}
@keyframes text-animation {
    0% {
        opacity: 0;
    }

    100% {
        opacity: 1;
    }
}
.logo-animation {
    /* height: 600px; */
    height: 100vh;
    width: 50%;
}
.letter {
    user-select: none;
    opacity: 0;
    position: absolute;
    font-size: 500px;
    font-weight: bold;
    font-style: italic;
    margin: 0%;
    transition: .2s ease-out;

}
.a{
    z-index: 4;
    left: 1rem;
    animation: splash-animation .7s cubic-bezier(.47, -0.01, .66, .99) .1s forwards;
}
.b{
    z-index: 3;
    left: 2rem;
    animation: splash-animation .7s cubic-bezier(.47, -0.01, .66, .99) .2s forwards;
}
.c{
    z-index: 2;
    left: 3rem;
    animation: splash-animation .7s cubic-bezier(.47, -0.01, .66, .99) .3s forwards;
}
.d{
    z-index: 1;
    left: 4rem;
    animation: splash-animation .7s cubic-bezier(.47, -0.01, .66, .99) .4s forwards;
}
/*Pallete color selector*/
.colorful.a {
    color: var(--var-colorful-indigo);  
}
.colorful.b {
    color: var(--var-colorful-yellow);
}
.colorful.c {
    color: var(--var-colorful-red);
}
.colorful.d {
    color: var(--var-default-white);
}
.punchy.a {
    color: var(--var-punchy-blue);
}
.punchy.b {
    color: var(--var-punchy-magenta);
}
.punchy.c {
    color: var(--var-punchy-yellow);
}
.punchy.d {
    color: var(--var-default-white);
}
.soft.a {
    color: var(--var-soft-pink);
}
.soft.b {
    color: var(--var-soft-pink-strong);
}
.soft.c {
    color: var(--var-soft-purple);
}
.soft.d {
    color: var(--var-soft-gray);
}
.blood.a {
    color: var(--var-blood-pink);
}
.blood.b {
    color: var(--var-blood-red);
}
.blood.c {
    color: var(--var-blood-red-strong);
}
.blood.d {
    color: var( --var-blood-blood);
}
@keyframes splash-animation {
    0% {
        left: 50rem;
    }

    50% {
        opacity: 1;
    }

    100% {
        opacity: 1;
    }
}
</style>