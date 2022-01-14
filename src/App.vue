<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div>
    <router-view/>
  </div>
</template>

<script>
import 'bootstrap/dist/css/bootstrap.min.css'

export default ({
 
})
</script>
<style >
  .app{
    padding:3px;
    width: 40px;
    margin-top:2px;
    margin-bottom:3px;
    color:rgb(116, 17, 17)
    
  }
</style>
