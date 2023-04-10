<template>
  <div class="container">
    <div class="left-panel">
      <el-upload
        ref="upload"
        class="upload-demo"
        drag
        :action="uploadUrl"
        :multiple="true"
        :on-success="handleSuccess"
        :on-error="handleError"
        :before-upload="beforeUpload"
      >
        <i class="el-icon-upload"></i>
        <div class="el-upload__text">将文件拖到此处，或<em>点击上传</em></div>
        <div class="el-upload__tip">请上传wav格式的音频</div>
      </el-upload>
    </div>
    <div class="right-panel">
      <el-card class="box-card">
        <div class="clearfix">
          <span>结果显示</span>
        </div>
        <div>
          <!-- 在此处添加结果显示内容 -->
        </div>
      </el-card>
    </div>
  </div>
</template>

<style scoped> 
.upload-demo ::v-deep .el-upload-dragger{
  margin-top: 4%;
  height:300px;
  width:300px;
  line-height: 180px;
  border: 5px solid rgb(41, 184, 219);
  border-style: dashed;
  border-radius: 25px;
}
.upload-demo ::v-deep .el-icon-upload{
  margin: 25%;
  transform: scale(1.5);
}
.upload-demo ::v-deep .el-upload__text{
  font-size: 16px;
  margin-top: -40%;
}
.upload-demo ::v-deep .el-upload__tip{
  font-size: 14px;
  margin-top: -50%;
}


</style>

<style>
.container {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 400px;
  width: 1200px;
}

.left-panel{
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100%;
  width: 30%;
}

.right-panel{
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100%;
  width: 70%;
}

.box-card {
  width: 80%;
  margin-top: 20px;
}
</style>

<script>
export default {
  data() {
    return {
      headers: {
        'Content-Type': 'multipart/form-data'
      },
      formData: new FormData(),
      uploadUrl: 'http://127.0.0.1:8081/upload_audio'
    }
  },
  methods: {
    handleSuccess(response, file, fileList) {
      // 处理上传成功的回调
      this.$message.success('上传成功')
      console.log(response, file, fileList)
    },
    handleError(error, file, fileList) {
      // 处理上传失败的回调
      this.$message.error('上传失败')
      console.log(error, file, fileList)
    },
    beforeUpload(file) {
      this.formData.append('file', file);
      this.formData.append('headers', JSON.stringify(this.headers));
      this.$refs.upload.$el.children[0].children[0].setAttribute('name', 'file');
    }
  }
}
</script>
