<template>
  <TodoCard>
    <el-row>
      <el-row>
        <h5>添加任务</h5>
      </el-row>
      <el-row>
        <el-input
          placeholder="请输入内容"
          v-model="inputText"
          @keyup.native="inputUp"
        ></el-input>
      </el-row>
      <el-row type="flex" justify="space-around">
        <el-col :span="4" class="todo_font"
          >{{ CopleteCount }}个任务未完成</el-col
        >
        <el-col :span="3" :offset="3">
          <el-button
            type="primary"
            size="small"
            class="allTask"
            @click="AllTask"
          >
            所有任务
          </el-button>
        </el-col>
        <el-col :span="3">
          <el-button type="danger" size="small" @click="unfinished"
            >未完成的任务</el-button
          >
        </el-col>
        <el-col :span="3">
          <el-button type="success" size="small" @click="finished"
            >已完成的任务</el-button
          >
        </el-col>
      </el-row>
    </el-row>

    <el-row>
      <div class="taskList">任务列表:</div>
      <TodoListBox
        @checkBoxClick="changeComplete"
        :TaskList="TempTask"
        @removeTaskItem="removeTaskItem"
      >
      </TodoListBox>
    </el-row>
  </TodoCard>
</template>

<script>
import TodoCard from "./child/TodoCard";
import TodoListBox from "./child/TodoListBox";
export default {
  name: "TodoVier",
  components: {
    TodoCard,
    TodoListBox,
  },
  data() {
    return {
      TempTask: [],
      TaskList: [
        { title: "吃饭", isComplete: false },
        { title: "睡觉", isComplete: true },
        { title: "打豆豆", isComplete: false },
      ],
      CopleteCount: 0,
      inputText: "",
    };
  },
  created() {
    this.TempTask = this.TaskList;
    let newArr = this.TaskList.filter((item) => !item.isComplete);
    this.CopleteCount = newArr.length;
  },
  methods: {
    changeComplete(arr) {
      this.CopleteCount = arr.length;
    },
    AllTask() {
      this.TempTask = this.TaskList;
    },
    unfinished() {
      let newArr = this.TaskList.filter((item) => !item.isComplete);
      this.TempTask = newArr;
    },
    finished() {
      let newArr = this.TaskList.filter((item) => item.isComplete);
      this.TempTask = newArr;
    },
    inputUp($event) {
      if ($event.keyCode == 13) {
        this.CopleteCount++;
        this.TaskList.push({ title: this.inputText, isComplete: false });
        this.AllTask();
        $event.target.value = "";
      }
    },
    removeTaskItem() {
      this.CopleteCount--;
    },
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