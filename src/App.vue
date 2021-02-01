<template>
  <!-- <div id="nav">
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link>
  </div>
  <router-view/> -->
  <div>
    lol
    <card :toggle='toggle' :slidedir='slidedir'>
    </card>
    <div id="naviBut">

    <div class='left arrow' @click="toggle=!toggle;slidedir='rtl'"></div>
    <div class='right arrow' @click="toggle=!toggle;slidedir='ltr'"></div>
    </div>
    
  </div>
</template>
<script>
import card from './components/card'
export default {
  components: {card},
  data () {
    return {
      toggle:false,
    }
  }
}

</script>
@import '~styles/main.scss';
<style lang="scss">
$lft-rot: rotateZ(45deg);
$rht-rot: rotateZ(-45deg);
#naviBut{
  display: flex;
  justify-content: space-around;
  margin: 20px auto auto auto;
  width: 100px;
}
.arrow{
  width: 10px;
  height: 10px;
  border-bottom: 3px solid black;
  // border-right: 1px solid black;
  
  &.left{
    
    // background: green;
    border-left: 3px solid black;
    transform: $lft-rot;
  }

  &.right{
    border-right: 3px solid black;
    transform: $rht-rot;
  }

}

.left:hover{
  transform: scale(1.2)  $lft-rot; 
}
.right:hover{
  transform: scale(1.2)  $rht-rot; 
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
