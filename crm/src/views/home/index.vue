<template>
  <div class="home_container">
    <!-- <h1 style="text-align: center; color: red">{{ $route.meta.title }}</h1> -->
    <!-- <div class="menu-banner">
      <div class="menu-wrap">
        <ul>
          <li v-for="(item, index) in menuData" :key="index">
            <span ref="li" @mouseenter="enterEvent">{{ item.menuTitle }}</span>
          </li>
          <div class="b_liner" :style="style"></div>
        </ul>
      </div>
    </div> -->
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
import { menuData } from "./menuList";
export default {
  name: "home",
  components: {},
  data() {
    return {
      menuData: menuData,
      style: {
        width: 0,
        left: 0,
      },
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
    //  let li = this.$refs.li[0].getBoundingClientRect()
    //  let {x, y, height} = dom.getBoundingClientRect()
    //  console.log(x, y, height)
  },
  // 如果页面有keep-alive缓存功能，这个函数会触发
  activated() {},
  // 方法集合
  methods: {
    enterEvent(ev) {
      let dom = ev.target;
      let { x, y, width } = dom.getBoundingClientRect();
      this.style.width = width + "px";
      this.style.left = x + "px";
      console.log(dom.getBoundingClientRect());
    },
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
