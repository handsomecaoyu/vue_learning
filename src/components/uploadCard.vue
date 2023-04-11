<template>
  <el-card class="upload-card">
    <template #header>
      <div class="card-header">
        <span>上传音频</span>
      </div>
    </template>
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
  </el-card>
</template>


<style scoped> 
.upload-card ::v-deep {
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
.upload-card ::v-deep .el-card__body{
    height: 100%;
    padding: 0px;
}

.upload-demo ::v-deep{
    width: 100%;
    height: 100%;
}
.upload-demo ::v-deep .el-upload--text{
    width: 100%;
    height: 100%;
}

.upload-demo ::v-deep .el-upload-dragger{
    border: 0px;
    width: 100%;
    height: 100%;
}

.upload-demo ::v-deep .el-icon-upload{
    margin-top: 30%
}


</style>

<style>
.card-header{
  font-size: 20px;
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

