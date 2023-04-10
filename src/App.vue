<template>
  <el-container>
    <MyHeader></MyHeader>
    <MyBody></MyBody>
  </el-container>
</template>
<script>
import MyHeader from './components/MyHeader.vue'
import MyBody from './components/MyBody.vue'

export default {
  name: 'App',
  components: {
    MyHeader,
    MyBody
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
  margin-top: 0px;
}
</style>

<style scoped>
.el-container ::v-deep {
  flex-direction: column;
  margin: 0;
}
</style>
