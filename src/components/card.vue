<template>
    
        <transition :name="slidedir" mode="out-in" class="container">
            <div 
            v-if="toggle"
            >
            <div class="card "
            :class="{rotate:onHover}"
            @click="onHover=!onHover">
                <div class="front centered">
                    front1
                </div>
                <div class="back centered">
                    back1
                </div>
            </div>
            </div>
            <div 
            key="2"
            
            v-else>
                <div class="card"
                :class="{rotate:onHover}"
                @click="onHover=!onHover">
                <div class="front centered">
                    front2
                </div>
                <div class="back centered">
                    back2
                </div>
            </div>
            </div>
        </transition>
</template>

<script>
export default {
    props:['toggle','slidedir'],
    data () {
        return {
            onHover:false,   
            // toggle:false,
        }
    
    },
    watch:{
        toggle(){
            this.onHover=false;
        }
    }
}
</script>

<style lang='scss'>
.centered{
    display: flex;
    align-items: center;
    justify-content: center;
}
.container{
    display: flex;
    justify-content: center;
    height: 50vh;
    perspective: 500px;
}
.front{
    position: absolute;
    backface-visibility: hidden;
    width: 100%;
    height: 100%;
}
.back{
    position: absolute;
    backface-visibility: hidden;

    transform:rotateX(180deg) ;
    width: 100%;
    height: 100%;
}
.card{
    transform-style: preserve-3d;
    position: relative;
    display: flex;
    /* border:1px solid black; */
    box-shadow: none;
    width: 50vw;
    height: 50vh;
    /* min-width: 60vw; */
    background: pink;
    /* max-width: 80vw; */
    box-shadow: 2px 3px 10px 0px  black  !important;

transition: transform 1s ease-in-out,box-shadow 0.8s linear;
    /* padding: 10px; */
}

.rotate{
    transform: rotateX(180deg);
    box-shadow: 2px -3px 10px 0px  black  !important;
}

.rtl-enter-active,
.rtl-leave-active,
.ltr-enter-active,
.ltr-leave-active
{
  transition: opacity 0.40s linear,transform 0.40s linear;
}

.rtl-enter-from,
.rtl-leave-to, 
.ltr-enter-from,
.ltr-leave-to 
{
    /* transform: translateX(100px); */
    opacity: 0;
}
.rtl-leave-to,.ltr-enter-from{
    transform: translateX(-500px)scale(0.7);
    
}
.rtl-enter-from,.ltr-leave-to{
    transform: translateX(500px) scale(0.7);
    
}




</style>