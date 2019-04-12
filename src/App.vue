<template>
  <div id="app">
    <Header />
    <router-view/>
  </div>
</template>


<script>
import Header from './components/layouts/Header'
export default {
  name:'app',

  components : {
    Header
  }
}

</script>



<style>
/* there we put our global styles */
  * {
    box-sizing: border-box;
    padding: 0;
    margin: 0;
  }

  body { 
    font-size: inherit;
    font-family: Arial, Helvetica, sans-serif;
    line-height: 1.4;
  }

  .btn { 
    display: inline-block;
    border: none;
    background: #555 ;
    color: #fff; 
    padding: 7px 20px ; 
    cursor: pointer;
  }

  .btn:hover {
    background: #666;
  }
</style>
