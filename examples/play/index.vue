<template>
  <div style="margin: 20px;width:600px;">
    <!-- <el-input v-model="input" placeholder="请输入内容"></el-input> -->
    <el-date-picker
       size="medium"
      v-model="value1"
      type="daterange"
      range-separator="~"
      placeholder="请选择时间范围"
      style="width:220px;">
    </el-date-picker>
    <div>
     <el-date-picker
      type="dates"
      v-model="value2"
      placeholder="选择一个或多个日期">
    </el-date-picker>
    </div>
  
     <el-table
      :data="tableData"
      style="width: 100%">
      <el-table-column
        prop="date"
        label="日期"
        width="180">
      </el-table-column>
      <el-table-column
        prop="name"
        label="姓名"
        width="180">
      </el-table-column>
      <el-table-column
        prop="address" 
        label="地址">
        <template scope="scope">
          <el-tooltip effect="dark" :content="scope.row.address" placement="top" :hide-after="0" trigger="hover">
            <div class="text_ellipsis">{{scope.row.address}}</div>
          </el-tooltip>
        </template>
      </el-table-column>
    </el-table>

    <el-transfer v-model="value" :data="data"></el-transfer>
  </div>
</template>

<script>
  export default {
    data() {
      const generateData = _ => {
        const data = [];
        for (let i = 1; i <= 15; i++) {
          data.push({
            key: i,
            label: `备选项 ${ i }`,
            disabled: i % 4 === 0
          });
        }
        return data;
      };
      return {
        input: 'Hello Element UI!',
        value1:"",
        value2:"",
        tableData: [{
            date: '2016-05-02',
            name: '王小虎',
            address: '上海市普陀区金沙江路 1518 弄sfsdfsfdsfdsdfdsfdgdfbvbvccdfvfvfvdvvdvfdfdgdg'
          }, {
            date: '2016-05-04',
            name: '王小虎',
            address: '上海市普陀区金沙江路 1517 弄'
          }, {
            date: '2016-05-01',
            name: '王小虎',
            address: '上海市普陀区金沙江路 1519 弄'
          }, {
            date: '2016-05-03',
            name: '王小虎',
            address: '上海市普陀区金沙江路 1516 弄'
          }],
      
       data: generateData(),
        value: [1, 4]
      };
    }
  };
</script>
<style scoped>
.text_ellipsis{
  overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
    width:100%;
}
</style>