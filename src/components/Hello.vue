
<template>
  <el-upload action="http://localhost:3000/upload/single" name="single" :before-upload="beforeUpload" :on-success="handleSuccess" :on-error="handleError" list-type="picture">
    <el-button size="small" type="primary">点击上传</el-button>
    <div slot="tip" class="el-upload__tip">只能上传jpg/png文件 且不超过2kb</div>
  </el-upload>
</template>

<script>
export default {
  name: 'hello',
  methods: {
    beforeUpload(file) {
      const isImage = (file.type === 'image/jpeg' || file.type === 'image/png');
      const isLt2K = file.size / 1024 < 2;
      if (!isImage) {
        this.$message.error('上传头像图片只能是jpg/png格式!');
      }
      if (!isLt2K) {
        this.$message.error('上传头像图片大小不能超过2kb!');
      }
      return isImage && isLt2K;
    },
    handleSuccess() {
      this.$message.success('上传成功');
    },
    handleError(err) {
      this.$message.error(`上传失败: ${err}`);
    },
  },
};
</script>
