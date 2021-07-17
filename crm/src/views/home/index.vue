<template>
  <div class="home_container">
    <el-table
      ref="multipleTable"
      :data="tableData"
      tooltip-effect="dark"
      style="width: 100%"
      @selection-change="handleSelectionChange"
    >
      <el-table-column type="selection" width="55"> </el-table-column>
      <el-table-column label="日期" width="120">
        <template slot-scope="scope">{{ scope.row.date }}</template>
      </el-table-column>
      <el-table-column prop="name" label="姓名" width="120"> </el-table-column>
      <el-table-column prop="address" label="地址" show-overflow-tooltip>
      </el-table-column>
    </el-table>
  </div>
</template>
<script>
export default {
  name: "home",
  components: {},
  data() {
    return {
      left: 10,
      tableData: [
        {
          date: "2016-05-03",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1518 弄",
        },
        {
          date: "2016-05-02",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1518 弄",
        },
        {
          date: "2016-05-04",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1518 弄",
        },
        {
          date: "2016-05-01",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1518 弄",
        },
        {
          date: "2016-05-08",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1518 弄",
        },
        {
          date: "2016-05-06",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1518 弄",
        },
        {
          date: "2016-05-07",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1518 弄",
        },
      ],
      multipleSelection: [],
    };
  },
  computed: {},
  watch: {},
  created() {},
  mounted() {
  },
  // 如果页面有keep-alive缓存功能，这个函数会触发
  activated() {},
  // 方法集合
  methods: {
    handleSelectionChange(val) {
      console.log(this.$refs)
      if (val.length > 1) {
        this.$refs.multipleTable.clearSelection(); //清空列表的选中
        this.$refs.multipleTable.toggleRowSelection(val[val.length - 1]); //只显示选中最后一个 这时val还是多选的列表(就是你选中的几个数据)
      } else if (val.length === 1) {
        this.multipleTable = val[val.length - 1];
      } else {
        this.multipleTable = []; //this.multipleTable是选中行的最后一条数据
      }
    },
  },
};
</script>

<style lang="scss" scoped>
@import "~@/styles/home/index.scss";
</style>
