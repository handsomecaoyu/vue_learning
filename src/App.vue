<template>
  <el-container>
    <myHeader></myHeader>
    <classificationBody></classificationBody>
  </el-container>
</template>
<script>
import myHeader from './components/myHeader.vue'
import classificationBody from './components/classificationBody.vue'

export default {
  name: 'App',
  components: {
    classificationBody,
    myHeader
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
