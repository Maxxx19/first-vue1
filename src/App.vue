<!--<link rel="stylesheet" href="../node_modules/materialize-css/dist/css/materialize.min.css">-->
<template>
  <div id="app">
    <Navbar />
    <div>
      <div>
        <img alt="Vue logo" width="15%" src="./assets/logo.png">
      </div>
      <div>
        <router-link to="/home"> Home </router-link> <br>
      </div>
      <div>
        <router-link to="/hello">Hello</router-link>
      </div>

    </div>

    <router-view></router-view>

    <HelloWorld msg="Welcome to Your Vue.js App"/>
   <!-- <Hello msg="Hi! Welcome to first route"/>-->
    <Home :goes="goes" @delete-go="deleteGo"/>

  </div>
</template>

<script>
//import HelloWorld from './components/HelloWorld.vue'
//import Hello from './views/Hello.vue'
import Home from './views/Home.vue'
import Navbar from "./components/Navbar";
export default {
  name: 'App',
  data(){
    return {
      goes: ['Repeat after me','Do not touch it']
    }
  },
  components: {
   // HelloWorld
    Navbar,
    Home
  },
  methods: {
    deleteGo(index){
      this.goes.splice(index, 1);
    }
  }
}
</script>

<style lang="scss">

  @import "~materialize-css/dist/css/materialize.min.css";
  img{
    margin-top: 100px;
  }
</style>

//
