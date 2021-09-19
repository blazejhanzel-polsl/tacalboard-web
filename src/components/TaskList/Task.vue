<template>
  <div class="task">
    <input type="checkbox">
    <div>{{ task.title }}</div>
  </div>
</template>

<script>
export default {
  name: 'Task',
  props: {
    task: Object,
  },
};
</script>

<style lang="scss" scoped>
.task {
  background-color: #ffffff;
  border: solid #cccccc;
  border-width: 0px 0px 1px 0px;
  height: 50px;
}

.task:hover {
  background-color: #f5f5f5 !important;
}

.task > input {
  display: flex;
  float: left;
  height: 28px;
  margin: 11px 0px 0px 16px;
  width: 28px;
}

.task > div {
  display: flex;
  float: left;
  font-size: 18px;
  margin: 6px 0px 0px 11px;
}
</style>
