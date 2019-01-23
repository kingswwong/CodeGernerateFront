<template>
    <div id="steps">
      <el-steps :active="activeIndex" align-center>
        <el-step title="PackageMessage" description="Create PackageInfo"></el-step>
        <el-step title="Entity" description="Create Entity"></el-step>
        <el-step title="Repository" description="Create Repository"></el-step>
        <el-step title="Service" description="Create Service"></el-step>
        <el-step title="Controller" description="Create Controller"></el-step>
      </el-steps>
    </div>
</template>

<script>
  export default {
    name: "Steps",
    props:['activeIndex']
  }
</script>

<style scoped>

</style>
