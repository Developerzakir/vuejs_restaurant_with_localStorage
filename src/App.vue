<template>

  

  <router-view></router-view>
  
</template>

<script>


export default {
  name: 'App',
  components: {
   
    
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  
}


.register input, .login input, .add input, .update input{
    width: 350px;
    height: 45px;
    padding-left: 15px;
    display: block;
    margin-bottom: 18px;
    margin-right: auto;
    margin-left: auto;
    border: 1px solid skyblue;
}

.register button, .login button, .add button, .update button{
    width: 350px;
    height: 38px;
    border: 1px solid skyblue;
    background: navy;
    color: #fff;
    cursor: pointer;

}

.menu{
  background-color: #2c3e50;
  padding: 10px;
}

.menu a{
  display: inline-block;
  padding: 12px 10px;
  color: #fff;
  text-decoration: none;
}

.menu a:hover{
  background-color: gray;
  
}
</style>
