<template>
    <div id="generate" style="margin-top: 30px">
      <steps :activeIndex="activeIndex"></steps>
      <package-message v-show="activeIndex === 0" @addPackageInfo="addPackageInfo"></package-message>
      <entity v-show="activeIndex === 1" @addEntity="addEntity"></entity>
      <repository v-show="activeIndex === 2" ref="childRepository" @addRepository="addRepository"></repository>
    </div>
</template>

<script>
  import Steps from '@/components/Steps'
  import Entity from '@/components/Entity'
  import PackageMessage from '@/components/PackageMessage'
  import Repository from '@/components/Repository'
  export default {
    name: "Generate",
    components: {Steps, Entity, PackageMessage, Repository},
    data(){
      return{
        activeIndex: 0,
        entityData:[],
        repositoryData:[],
        packageInfo:{},
      }
    },
    methods:{
      next:function () {
        this.activeIndex++
      },
      addEntity:function (entityData) {
        this.entityData = entityData
        let initColumn = {
          funtionName: '',
          functionType: '',
          returnType: '',
          config:[]
        }
        for(let i = 0;i < entityData.length;i++){
          let temp = entityData[i].columnName
          let tempObject = {
            name: temp,
            value: false
          }
          initColumn.config.push(tempObject)
        }
        this.$refs.childRepository.initData(initColumn)
        this.activeIndex++
      },
      addPackageInfo:function (formInline) {
        this.packageInfo = formInline
        this.activeIndex++
      },
      addRepository: function (repositoryData) {
        this.repositoryData = repositoryData
        this.activeIndex++
        console.log(this.repositoryData)
      }
    }
  }
</script>

<style scoped>

</style>
