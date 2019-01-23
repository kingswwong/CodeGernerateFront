<template>
    <div id="packageMessage" style="margin-top:50px">
      <el-form :inline="true" :model="formInline" class="demo-form-inline">
        <el-form-item label="PackageName">
          <el-input v-model="formInline.packageName" placeholder="Input PackageName"></el-input>
        </el-form-item>
        <el-form-item label="TableName">
          <el-input v-model="formInline.tableName" placeholder="Input TableName"></el-input>
        </el-form-item>
        <el-form-item>
          <el-button type="primary" @click="onSubmit">Submit</el-button>
        </el-form-item>
      </el-form>
    </div>
</template>

<script>
  export default {
    name: "PackageMessage",
    data() {
      return {
        formInline: {
          packageName: '',
          tableName: ''
        }
      }
    },
    methods: {
      onSubmit() {
        this.$emit('addPackageInfo',this.formInline)
      }
    }
  }
</script>

<style scoped>

</style>
