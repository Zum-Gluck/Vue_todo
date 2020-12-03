<template>
  <main>
    <div class="header">任务计划列表</div>
    <div class="content">
      <slot></slot>
    </div>
  </main>
</template>

<script>
export default {
  name: "TodoCard",
};
</script>

<style lang="less" scoped>
@bgC: #347ab6;
main {
  width: 70%;
  height: 540px;
  margin: 0 auto;

  border: 1px @bgC solid;
  border-radius: 10px 10px 0 0;
  overflow: hidden;
  .header {
    height: 38px;
    padding-left: 18px;
    font: 14px / 36px "MicrosoftYaHei";
    color: #fff;
    background-color: @bgC;
  }
  .content {
    padding: 10px;
  }
}
</style>