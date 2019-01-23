<template>
  <div class="hello">
    <navbar></navbar>
    <div style="text-align: center" v-show="!generateShow">
      <h1>Welcome to CodeGenerate</h1>
      <el-button type="primary" @click="showGenerate">Start</el-button>
    </div>
    <generate v-show="generateShow"></generate>
  </div>
</template>

<script>
  import Navbar from '@/components/NavBar'
  import Generate from '@/components/Generate'
export default {
  name: 'HelloWorld',
  components: {Navbar,Generate},
  data(){
    return{
      generateShow: false
    }
  },
  methods:{
    showGenerate:function () {
      this.generateShow = true
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
