<template>
  <TodoCard>
    <el-row>
      <h5>添加任务</h5>
    </el-row>
    <el-row>
      <el-input v-model="input" placeholder="请输入内容"></el-input>
    </el-row>
    <el-row type="flex" justify="space-around">
      <el-col :span="4" class="todo_font">2个任务未完成</el-col>
      <el-col :span="3" offset="3">
        <el-button type="primary" size="small" class="allTask"
          >所有任务</el-button
        >
      </el-col>
      <el-col :span="3">
        <el-button type="danger" size="small">未完成的任务</el-button>
      </el-col>
      <el-col :span="3">
        <el-button type="success" size="small">已完成的任务</el-button>
      </el-col>
    </el-row>

    <el-row>
      <div class="taskList">任务列表:</div>
    </el-row>
  </TodoCard>
</template>

<script>
import TodoCard from "./child/TodoCard";
export default {
  name: "TodoVier",
  components: {
    TodoCard,
  },
};
</script>

<style lang="less" >
@bgC: #347ab6;
.el-row {
  margin-bottom: 10px;
}
.el-input__inner {
  height: 27px !important;
}
.el-col {
  text-align: center;
}
.todo_font {
  display: flex;
  align-items: center;
  font-size: 13px;
  color: red;
}
.allTask {
  background-color: @bgC !important;
  border-color: @bgC !important;
}
.taskList {
  font-size: 22px;
}
</style>