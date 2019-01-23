<template>
    <div id="navbar">
      <el-menu :default-active="'1'" class="el-menu-demo" mode="horizontal" @select="handleSelect">
        <el-menu-item index="1">CodeGenerate</el-menu-item>
      </el-menu>
    </div>
</template>

<script>
  export default {
    name: "NavBar"
  }
</script>

<style scoped>

</style>
