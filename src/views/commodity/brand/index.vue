<template>
  <div class="app-container">
    <el-card class="search-card">
      <div>
        <div>
          <i class="el-icon-search"/>
          <span>筛选搜索</span>
        </div>
        <!-- 表单 -->
        <el-form ref="form" :model="listQuery" label-width="150px" size="small">
          <el-form-item label="品牌名称" style="float: left;">
            <el-input v-model="listQuery.nameKeyword"/>
          </el-form-item>
          <el-form-item label="品牌首字母" style="float: left;">
            <el-select v-model="listQuery.acronymKeyword" placeholder="请选择首字母缩写词">
              <el-option label="区域一" value="shanghai"/>
              <el-option label="区域二" value="beijing"/>
            </el-select>
          </el-form-item>
        </el-form>

        <el-button
          style="float: right"
          type="primary"
          size="small"
          icon="el-icon-search"
          @click="searchBrandList()">
          搜索
        </el-button>
      </div>
    </el-card>
    <el-card class="table-card">
      <i class="el-icon-document"/>
      <span>品牌列表</span>
      <el-button
        style="float: right; margin-right: 40px"
        class="search-button"
        type="success"
        size="mini"
        icon="el-icon-plus"
        @click="addBrand">
        新增
      </el-button>
      <template>
        <el-table
          :data="tableData"
          style="width: 100%;">
          <el-table-column type="selection" width="60" align="center"/>
          <el-table-column
            prop="id"
            label="编号"
            width="120"/>
          <el-table-column
            prop="name"
            label="品牌名称"
            width="320"/>
          <el-table-column
            prop="initial"
            label="品牌首字母"
            width="120"/>
          <el-table-column
            prop="sort"
            label="排序"
            width="120"/>
          <el-table-column
            prop="isShow"
            label="是否显示"
            width="120">
            <template slot-scope="scope">
              <el-switch
                :active-value="1"
                :inactive-value="0"
                v-model="scope.row.showStatus"
                @change="handleShowStatusChange(scope.$index, scope.row)"/>
            </template>
          </el-table-column>
          <el-table-column
            fixed="right"
            label="操作"
            width="180">
            <template slot-scope="scope">
              <el-button
                size="mini"
                type="info"
                @click="modifyBrand(scope.$index, scope.row)">编辑</el-button>
              <el-button
                size="mini"
                type="danger"
                @click="handleDelete(scope.$index, scope.row)">删除</el-button>
            </template>
          </el-table-column>
        </el-table>
      </template>
      <div class="batch-operate-container">
        <el-select
          v-model="operateType"
          size="mini"
          placeholder="批量操作">
          <el-option
            v-for="item in opeTypes"
            :key="item.value"
            :label="item.label"
            :value="item.value"/>
        </el-select>
        <el-button
          style="margin-left: 10px"
          class="search-button"
          type="primary"
          size="mini"
          @click="handleBatchOperate()">
          确定
        </el-button>
      </div>
      <div class="nav-bar-container">
        <el-pagination
          :page-size="listQuery.pageSize"
          :page-sizes="[5,10,15]"
          :current-page.sync="listQuery.pageNum"
          :total="total"
          background
          layout="total, jumper, prev, pager, next, sizes"
          @size-change="handleSizeChange"
          @current-change="handleCurrentChange"/>
      </div>
    </el-card>
  </div>
</template>

<script>
export default {
  name: 'Brand',
  data() {
    return {
      listQuery: {
        nameKeyword: null,
        acronymKeyword: null,
        pageNum: 1,
        pageSize: 10
      },
      tableData: [{
        date: '2016-05-03',
        name: '王小虎',
        province: '上海',
        city: '普陀区',
        address: '上海市普陀区金沙江路 1518 弄',
        zip: 200333
      }, {
        date: '2016-05-02',
        name: '王小虎',
        province: '上海',
        city: '普陀区',
        address: '上海市普陀区金沙江路 1518 弄',
        zip: 200333
      }, {
        date: '2016-05-04',
        name: '王小虎',
        province: '上海',
        city: '普陀区',
        address: '上海市普陀区金沙江路 1518 弄',
        zip: 200333
      }, {
        date: '2016-05-01',
        name: '王小虎',
        province: '上海',
        city: '普陀区',
        address: '上海市普陀区金沙江路 1518 弄',
        zip: 200333
      }, {
        date: '2016-05-08',
        name: '王小虎',
        province: '上海',
        city: '普陀区',
        address: '上海市普陀区金沙江路 1518 弄',
        zip: 200333
      }, {
        date: '2016-05-06',
        name: '王小虎',
        province: '上海',
        city: '普陀区',
        address: '上海市普陀区金沙江路 1518 弄',
        zip: 200333
      }, {
        date: '2016-05-07',
        name: '王小虎',
        province: '上海',
        city: '普陀区',
        address: '上海市普陀区金沙江路 1518 弄',
        zip: 200333
      }]
    }
  },
  created() {

  },
  methods: {
    searchBrandList() {

    },
    addBrand() {
      this.$router.push({path: '/commodity/addBrand'})
    },
    modifyBrand() {
      this.$router.push({path: '/commodity/modifyBrand'})
    }
  }
}
</script>

<style rel="stylesheet/scss" lang="scss">
  .el-table {
    text-align: center;
  }
  .el-table th>.cell {
    text-align: center;
  }
  .table-card {
    margin-top: 10px;
  }
  .batch-operate-container {
    margin-top: 20px;
  }
  //批量操作栏样式
  .batch-operate-container {
    display: inline-block;
    margin-top: 20px;
  }

  //分页栏样式
  .nav-bar-container {
    display: inline-block;
    float: right;
    margin-top: 20px;
  }
</style>
