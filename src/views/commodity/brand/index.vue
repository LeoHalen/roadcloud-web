<template>
  <div class="app-container">
    <el-card class="search-card">
      <div>
        <i class="el-icon-search"></i>
        <span>筛选搜索</span>
        <!-- 表单 -->
        <el-form ref="form" :model="listQuery" label-width="80px">
          <el-form-item label="品牌名称">
            <el-input v-model="listQuery.nameKeyword"></el-input>
          </el-form-item>
          <el-form-item label="品牌首字母">
            <el-select v-model="listQuery.acronymKeyword" placeholder="请选择首字母缩写词">
              <el-option label="区域一" value="shanghai"></el-option>
              <el-option label="区域二" value="beijing"></el-option>
            </el-select>
          </el-form-item>
        </el-form>

        <el-button
          style="float: right"
          @click="searchBrandList()"
          type="primary"
          size="small">
          查询结果
        </el-button>
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
        }
      }
    },
    methods:{
      searchBrandList() {

      },
    }
  }
</script>
