<template>
    <div id="entity">
      <div style="margin-top: 10px">
        <el-button type="primary" @click="addRow">Add</el-button>
        <el-button type="primary" @click="submitEntity">Next</el-button>
      </div>
      <el-table :data="tableData3" style="width: 90%;margin-left: 5%" >
        <el-table-column prop="columnName" label="ColumnName" width="300" align="center">
          <template slot-scope="scope">
            <el-input  v-model="scope.row.columnName" placeholder="字段名称"></el-input>
          </template>
        </el-table-column>
        <el-table-column prop="columnType" label="ColumnType" width="300" align="center">
          <template slot-scope="scope">
            <el-select v-model="scope.row.columnType" placeholder="请选择">
              <el-option
                v-for="item in options"
                :key="item"
                :label="item"
                :value="item">
              </el-option>
            </el-select>
          </template>
        </el-table-column>
        <el-table-column  label="Config" align="center">
          <el-table-column  label="IsPrimaryKey" align="center">
            <template slot-scope="scope">
              <el-checkbox  v-model="scope.row.isPrimaryKey" @change="isPrimaryBind(scope.$index)"></el-checkbox>
            </template>
          </el-table-column>
          <el-table-column  label="NotNull" align="center">
            <template slot-scope="scope">
              <el-checkbox  v-model="scope.row.notNull"></el-checkbox>
            </template>
          </el-table-column>
          <el-table-column  label="IsUnique" align="center">
            <template slot-scope="scope">
              <el-checkbox  v-model="scope.row.isUnique"></el-checkbox>
            </template>
          </el-table-column>
          <el-table-column  label="AutoInc" align="center">
            <template slot-scope="scope">
              <el-checkbox  v-model="scope.row.autoInc"></el-checkbox>
            </template>
          </el-table-column>
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
    name: "Entity",
    data(){
      return{
        tableData3:[
          {
            columnName: '',
            columnType: '',
            isPrimaryKey: false,
            notNull: false,
            isUnique: false,
            autoInc: false,
          }
        ],
        options:[
          'VARCHAR',
          'INTEGER',
          'BIT',
          'DATE'
        ]
      }
    },
    methods:{
      addRow:function () {
        this.tableData3.push({
          columnName: '',
          columnType: '',
          isPrimaryKey: false,
          notNull: false,
          isUnique: false,
          autoInc: false,
        })
      },
      deleteRow:function (index) {
        this.$confirm('是否删除此行?', '提示', {
          confirmButtonText: '确定',
          cancelButtonText: '取消',
          type: 'warning'
        }).then(() => {
          this.tableData3.splice(index,1)
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
      submitEntity:function () {
        this.$emit('addEntity',this.tableData3)
      },
      isPrimaryBind: function (index) {
        this.tableData3[index].notNull = true
      }
    }
  }
</script>

<style scoped>

</style>
