<template>
  <div>
    <table>
      <tbody>
        <tr
          v-for="(item, index) in TaskList"
          :key="index"
          :class="{ isComplete: item.isComplete }"
          @mouseenter="trHover"
          @mouseleave="trLeave"
        >
          <td>
            <input
              type="checkbox"
              v-model="item.isComplete"
              @click="iptClick(item.isComplete)"
            />
            {{ item.title }}

            <span
              class="iconfont icon-delete delete"
              @click="removeTask(index)"
            >
            </span>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  props: ["TaskList"],
  data() {
    return {};
  },
  data() {
    return {};
  },
  methods: {
    iptClick(flag) {
      setTimeout(() => {
        let newArr = this.TaskList.filter((item) => !item.isComplete);
        this.$emit("checkBoxClick", newArr);
      }, 200);
    },
    trHover($event) {
      let currentEl = $event.target;
      currentEl.style.backgroundColor = "#eee";
      currentEl.children[0].lastElementChild.style.display = "block";
    },
    trLeave($event) {
      let currentEl = $event.target;
      currentEl.style.backgroundColor = "";
      currentEl.children[0].lastElementChild.style.display = "none";
    },
    removeTask(index) {
      this.TaskList.splice(index, 1);
      this.$emit("removeTaskItem");
    },
  },
};
</script>

<style lang="less" scoped>
table {
  width: 100%;
  border-spacing: 0;
  border-collapse: collapse;
  margin-top: 10px;
  tbody {
    width: 100%;
    tr {
      width: 100%;
    }
    td {
      width: 100%;
      height: 35px;
      border: 1px solid #ccc;
      padding-left: 20px;
      input {
        margin-right: 7px;
      }
      .delete {
        display: none;
        float: right;
        margin-right: 40px;
        color: #f78989;
        font-size: 18px;
        cursor: pointer;
      }
    }
  }
}

.isComplete {
  text-decoration: line-through;
}
</style>