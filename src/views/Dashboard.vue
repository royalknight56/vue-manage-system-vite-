<template>
  <div>
    <el-row :gutter="20">
      <el-col :span="8">
        <el-card shadow="hover" class="mgb20" style="height: 252px">
          <div class="user-info">
            <img src="../assets/img/touxiang.png" class="user-avator" alt />
            <div class="user-info-cont">
              <div class="user-info-name">{{ name }}</div>
              <div>{{ role }}</div>
            </div>
          </div>
          <div class="user-info-list">
            上次登录时间：
            <span>2021-04-03</span>
          </div>
          <div class="user-info-list">
            上次登录地点：
            <span>西安</span>
          </div>
        </el-card>
        <el-card shadow="hover" style="height: 252px">
          <template #header>
            <div class="clearfix">
              <span>任务进度</span>
            </div>
          </template>
          前台
          <el-progress :percentage="71.3" color="#42b983"></el-progress>后台
          <el-progress :percentage="24.1" color="#f1e05a"></el-progress>运营
          <el-progress :percentage="13.7"></el-progress>产品
          <el-progress :percentage="5.9" color="#f56c6c"></el-progress>
        </el-card>
      </el-col>
      <el-col :span="16">
        <el-row :gutter="20" class="mgb20">
          <el-col :span="8">
            <el-card shadow="hover" :body-style="{ padding: '0px' }">
              <div class="grid-content grid-con-1">
                <i class="el-icon-user-solid grid-con-icon"></i>
                <div class="grid-cont-right">
                  <div class="grid-num">1234</div>
                  <div>用户访问量</div>
                </div>
              </div>
            </el-card>
          </el-col>
          <el-col :span="8">
            <el-card shadow="hover" :body-style="{ padding: '0px' }">
              <div class="grid-content grid-con-2">
                <i class="el-icon-message-solid grid-con-icon"></i>
                <div class="grid-cont-right">
                  <div class="grid-num">321</div>
                  <div>系统消息</div>
                </div>
              </div>
            </el-card>
          </el-col>
          <el-col :span="8">
            <el-card shadow="hover" :body-style="{ padding: '0px' }">
              <div class="grid-content grid-con-3">
                <i class="el-icon-s-goods grid-con-icon"></i>
                <div class="grid-cont-right">
                  <div class="grid-num">5000</div>
                  <div>数量</div>
                </div>
              </div>
            </el-card>
          </el-col>
        </el-row>
        <el-card shadow="hover" style="height: 403px">
          <template #header>
            <div class="clearfix">
              <span>待办事项</span>
              <el-button style="float: right; padding: 3px 0" type="text"
                >添加</el-button
              >
            </div>
          </template>

          <el-table :show-header="false" :data="todoList" style="width: 100%">
            <el-table-column width="40">
              <template #default="scope">
                <el-checkbox v-model="scope.row.status"></el-checkbox>
              </template>
            </el-table-column>
            <el-table-column>
              <template #default="scope">
                <div
                  class="todo-item"
                  :class="{
                    'todo-item-del': scope.row.status,
                  }"
                >
                  {{ scope.row.title }}
                </div>
              </template>
            </el-table-column>
            <el-table-column width="60">
              <template>
                <i class="el-icon-edit"></i>
                <i class="el-icon-delete"></i>
              </template>
            </el-table-column>
          </el-table>
        </el-card>
      </el-col>
    </el-row>
    <el-row :gutter="20">
      <el-col :span="12">
        <el-card shadow="hover">
          <ichart :option="optionUser"></ichart>
          <!-- <div id="chart1"></div> -->
          <!-- <schart ref="bar" class="schart" canvasId="bar" :options="options"></schart> -->
        </el-card>
      </el-col>
      <el-col :span="12">
        <el-card shadow="hover">
          <ichart :option="option3"></ichart>
          <!-- <schart ref="line" class="schart" canvasId="line" :options="options2"></schart> -->
        </el-card>
      </el-col>
    </el-row>
  </div>
</template>
<script setup>
import { inject, onMounted, reactive } from "vue";
import mychartcom from "../components/Header.vue";
import ichart from "../components/ichart.vue";
let todoList = reactive([
  {
    title: "前端页面需要完成",
    status: false,
  },
  {
    title: "仓库管理员运送货物",
    status: false,
  },
  {
    title: "财务统计财报",
    status: false,
  },
  {
    title: "运营完成今日份的推广",
    status: false,
  },
  {
    title: "产品做ppt",
    status: true,
  },
  {
    title: "今天出席会议",
    status: true,
  },
]);
let datalist = reactive([
  {
    name: "2018/09/04",
    value: 1083,
  },
  {
    name: "2018/09/05",
    value: 941,
  },
  {
    name: "2018/09/06",
    value: 1139,
  },
  {
    name: "2018/09/07",
    value: 816,
  },
  {
    name: "2018/09/08",
    value: 327,
  },
  {
    name: "2018/09/09",
    value: 228,
  },
  {
    name: "2018/09/10",
    value: 1065,
  },
]);
let optionUser = reactive({
  title: { text: "总用户量" },
  tooltip: {},
  xAxis: {
    data: ["12-3", "12-4", "12-5", "12-6", "12-7", "12-8"],
  },
  yAxis: {},
  series: [
    {
      name: "用户量",
      type: "line",
      data: [5, 20, 36, 10, 10, 20],
    },
  ],
});

let option2 = reactive({
  title: {
    text: "最近几个月各品类销售趋势图",
  },
  xAxis: {
    data: ["6月", "7月", "8月", "9月", "10月"],
  },
  yAxis: {},
  series: [
    {
      name: "家电",
      type: "line",
      data: [234, 278, 270, 190, 230],
    },
    {
      name: "百货",
      type: "line",
      data: [164, 178, 150, 135, 160],
    },
    {
      name: "食品",
      type: "line",
      data: [74, 118, 200, 235, 90],
    },
  ],
});
let option3 = reactive({
  title: {
    text: "最近一周各品类销售图",
  },
  xAxis: {
    data: ["周一", "周二", "周三", "周四", "周五"],
  },
  yAxis: {
  },
  legend: {
        data: ['家电', '百货','食品']
    },
  series: [
    {
      name: "家电",
      type: "bar",
      data: [234, 278, 270, 190, 230],
    },
    {
      name: "百货",
      type: "bar",
      data: [164, 178, 150, 135, 160],
    },
    {
      name: "食品",
      type: "bar",
      data: [74, 118, 200, 235, 90],
    },
  ],
});
let changeDate = function () {
  const now = new Date().getTime();
  datalist.forEach((item, index) => {
    const date = new Date(now - (6 - index) * 86400000);
    item.name = `${date.getFullYear()}/${
      date.getMonth() + 1
    }/${date.getDate()}`;
  });
};
</script>
<script>
// import  Schart from "vue-schart";
// console.log(Schart)
export default {
  name: "dashboard",
  data() {
    return {
      name: localStorage.getItem("ms_username"),

      options: {
        type: "bar",
        title: {
          text: "最近一周各品类销售图",
        },
        xRorate: 25,
        labels: ["周一", "周二", "周三", "周四", "周五"],
        datasets: [
          {
            label: "家电",
            data: [234, 278, 270, 190, 230],
          },
          {
            label: "百货",
            data: [164, 178, 190, 135, 160],
          },
          {
            label: "食品",
            data: [144, 198, 150, 235, 120],
          },
        ],
      },
    };
  },
  components: {
    // Schart
  },
  computed: {
    role() {
      return this.name === "admin" ? "超级管理员" : "普通用户";
    },
  },

  methods: {},
};
</script>

<style scoped>
.el-row {
  margin-bottom: 20px;
}

.grid-content {
  display: flex;
  align-items: center;
  height: 100px;
}

.grid-cont-right {
  flex: 1;
  text-align: center;
  font-size: 14px;
  color: #999;
}

.grid-num {
  font-size: 30px;
  font-weight: bold;
}

.grid-con-icon {
  font-size: 50px;
  width: 100px;
  height: 100px;
  text-align: center;
  line-height: 100px;
  color: #fff;
}

.grid-con-1 .grid-con-icon {
  background: rgb(45, 140, 240);
}

.grid-con-1 .grid-num {
  color: rgb(45, 140, 240);
}

.grid-con-2 .grid-con-icon {
  background: rgb(100, 213, 114);
}

.grid-con-2 .grid-num {
  color: rgb(45, 140, 240);
}

.grid-con-3 .grid-con-icon {
  background: rgb(242, 94, 67);
}

.grid-con-3 .grid-num {
  color: rgb(242, 94, 67);
}

.user-info {
  display: flex;
  align-items: center;
  padding-bottom: 20px;
  border-bottom: 2px solid #ccc;
  margin-bottom: 20px;
}

.user-avator {
  width: 120px;
  height: 120px;
  border-radius: 50%;
}

.user-info-cont {
  padding-left: 50px;
  flex: 1;
  font-size: 14px;
  color: #999;
}

.user-info-cont div:first-child {
  font-size: 30px;
  color: #222;
}

.user-info-list {
  font-size: 14px;
  color: #999;
  line-height: 25px;
}

.user-info-list span {
  margin-left: 70px;
}

.mgb20 {
  margin-bottom: 20px;
}

.todo-item {
  font-size: 14px;
}

.todo-item-del {
  text-decoration: line-through;
  color: #999;
}

.schart {
  width: 100%;
  height: 300px;
}
#chart1 {
  width: 100%;
  height: 300px;
}
</style>
