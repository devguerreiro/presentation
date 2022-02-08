<template lang='pug'>
#app
  #logo-ifc <img src="@/logo-ifc.png" alt="Logo IFC" height="75" width="250">
  #logo-vuejs <img src="@/logo-vuejs.png" alt="Logo Vue.js" height="75" width="100">
  router-view
</template>

<script>
export default {
  name: 'app'
}
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  #logo-ifc {
    position: absolute;
    top: 50px;
    left: 100px;
    z-index: 2;
  }
  #logo-vuejs {
    position: absolute;
    top: 50px;
    right: 100px;
    z-index: 2;
  }
}
</style>
