<template>
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
    <div class="el-upload__tip">上传你的文件</div>
  </el-upload>
</template>

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
