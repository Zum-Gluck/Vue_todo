<template>
  <div>
    <table>
      <tbody>
        <tr
          v-for="(item, index) in TaskList"
          :key="index"
          :class="{ isComplete: item.isComplete }"
        >
          <td>
            <input
              type="checkbox"
              v-model="item.isComplete"
              @click="iptClick(item.isComplete)"
            />
            {{ item.title }}
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
  methods: {
    iptClick(flag) {
      setTimeout(() => {
        let newArr = this.TaskList.filter((item) => !item.isComplete);
        this.$emit("checkBoxClick", newArr);
      }, 200);
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
    }
  }
}

.isComplete {
  text-decoration: line-through;
}
</style>