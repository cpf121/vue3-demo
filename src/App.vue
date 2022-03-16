<template>
  <div id="nav">
    <floatball :operates="operates"></floatball>
  </div>
</template>
<script>
import floatball from './components/float-ball'
export default {
  components: {
    floatball
  },
  setup(){
    const operates=[{
      name:"todo-list-o",
      operateName:"addTable",
      content:"新增",
      size:20
    },{
      name:"balance-list-o",
      operateName:"batch",
      content:"批量",
      size:20
    }]
    return{
      operates
    }
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

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
