<template>
    <div id="repository">
      <div style="margin-top: 10px">
        <el-button type="primary" @click="addRow">Add</el-button>
        <el-button type="primary" @click="addRepository">Next</el-button>
      </div>
      <el-table :data="repositoryData" style="width: 90%;margin-left: 5%" >
        <el-table-column prop="functionName" label="FunctionName" width="200" align="center">
          <template slot-scope="scope">
            <el-input  v-model="scope.row.functionName" placeholder="输入方法名"></el-input>
          </template>
        </el-table-column>
        <el-table-column prop="functionType" label="FunctionType" width="200" align="center">
          <template slot-scope="scope">
            <el-select v-model="scope.row.functionType" placeholder="请选择方法类型">
              <el-option
                v-for="item in options"
                :key="item"
                :label="item"
                :value="item">
              </el-option>
            </el-select>
          </template>
        </el-table-column>
        <el-table-column prop="returnType" label="ReturnType" width="200" align="center">
          <template slot-scope="scope">
            <el-input  v-model="scope.row.returnType" placeholder="输入返回类型"></el-input>
          </template>
        </el-table-column>
        <el-table-column v-for="( item, index ) in config" :key="index" :label="item.name" align="center">
          <template slot-scope="scope">
            <el-checkbox v-model="scope.row.config[index].value"></el-checkbox>
          </template>
        </el-table-column>
        <el-table-column label="Options" align="center">
          <template slot-scope="scope">
            <i class="el-icon-delete" @click="deleteRow(scope.$index)"></i>
          </template>
        </el-table-column>
      </el-table>
    </div>
</template>

<script>
  export default {
    name: "Repository",
    data(){
      return{
        repositoryData:[],
        config:[],
        options:['INSERT','DELETE','UPDATE','FIND']
      }
    },
    methods:{
      initData:function (columnData) {
        this.config = columnData.config
        this.repositoryData.push(columnData)
      },
      addRow(){
        let rowData = {
          functionName: '',
          functionType: '',
          returnType: '',
          config:[]
        }
        for(let i = 0;i < this.config.length;i++){
          let temp = this.config[i].name
          let tempObject = {
            name: temp,
            value: false
          }
          rowData.config.push(tempObject)
        }
        this.repositoryData.push(rowData)

      },
      deleteRow:function (index) {
        this.$confirm('是否删除此行?', '提示', {
          confirmButtonText: '确定',
          cancelButtonText: '取消',
          type: 'warning'
        }).then(() => {
          this.repositoryData.splice(index,1)
          this.$message({
            type: 'success',
            message: '删除成功!'
          });
        }).catch(() => {
          this.$message({
            type: 'info',
            message: '已取消删除'
          });
        });
      },
      addRepository:function () {
        this.$emit('addRepository',this.repositoryData)
      }
    }
  }
</script>

<style scoped>

</style>
