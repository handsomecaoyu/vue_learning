<template>
<!-- main -->
<el-main>
  <div class="container">
    <!-- 左侧用于音频上传 -->
    <div class="left-panel">
      <uploadCard></uploadCard>
    </div>
  <div class="right-panel">
      <resultCard></resultCard>
  </div>
</div>
</el-main>
  
</template>

<script>
import uploadCard from './uploadCard.vue'
import resultCard from './resultCard.vue'

export default {
  name: 'App',
  components: {
    uploadCard,
    resultCard
  }
}
</script>

<style>
/* 主体样式 */
.el-main{
  background-color: rgb(247, 247, 247);
  height: 700px;
  width: 100%;
}

/* 包装音频上传和识别结果的容器 */
.container {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
  width: 100%;
}

/* 左侧用于音频上传 */
.left-panel{
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  margin-left: 10%;
  margin-right: 2%;
  padding: 0;
  width: 30%;
}

/* 右侧用于结果显示 */
.right-panel{
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  margin-right: 10%;
  margin-left: 2%;
  padding: 0;
  width: 70%;
}

</style>

