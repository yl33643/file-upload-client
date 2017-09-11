
<template>
  <el-upload action="http://localhost:3000/upload/single" name="single" :before-upload="beforeUpload" :on-success="handleSuccess" :on-error="handleError" list-type="picture">
    <el-button size="small" type="primary">点击上传</el-button>
    <div slot="tip" class="el-upload__tip">只能上传jpg文件，且不超过2MB</div>
  </el-upload>
</template>

<script>
export default {
  name: 'hello',
  methods: {
    beforeUpload(file) {
      const isJPG = file.type === 'image/jpeg';
      const isLt2M = file.size / 1024 / 1024 < 2;
      if (!isJPG) {
        this.$message.error('上传头像图片只能是JPG格式!');
      }
      if (!isLt2M) {
        this.$message.error('上传头像图片大小不能超过2MB!');
      }
      return isJPG && isLt2M;
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
