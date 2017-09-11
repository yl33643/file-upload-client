
<template>
  <el-upload action="http://localhost:3000/upload/single" name="single" :on-success="handleSuccess" :on-error="handleError" list-type="picture">
    <el-button size="small" type="primary">点击上传</el-button>
  </el-upload>
</template>

<script>
export default {
  name: 'hello',
  methods: {
    handleSuccess() {
      this.$message.success('上传成功');
    },
    handleError(err) {
      this.$message.error(`上传失败: ${err}`);
    },
  },
};
</script>
