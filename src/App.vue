<template>
  <HelloWorld/>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  }
}
</script>

<style>

*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-weight: 500; 
}

#app{
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  color: #fff;
  font-family:'Quicksand Light', sans-serif; 
  text-align: center;
  background: url('./assets/415a774c752bafc2c97499a733a41151.gif');
  background-size: cover;
  background-position: bottom;
  
}

</style>
