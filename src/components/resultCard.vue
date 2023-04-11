<template>
    <el-card class="result-card">
    <template #header>
      <div class="card-header">
        <span>识别结果</span>
      </div>
    </template>
      <div>
        <!-- 在此处添加结果显示内容 -->
      </div>
    </el-card>
</template>

<style scoped>
  .result-card ::v-deep{
    display: flex;
    flex-direction: column;
    margin: 5%;
    height: 400px;
    width: 100%;
    border: 0px;
    border-radius: 15px;
    background-color: white;
    box-shadow: 1px 1px 20px rgba(0,0,0,0.15) !important;
  }
</style>