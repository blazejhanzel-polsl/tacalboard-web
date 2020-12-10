<template>
  <div id="body">
    <Sidebar />
    <Content />
  </div>
</template>

<script>
import Sidebar from '@/components/TaskList/Sidebar.vue';
import Content from '@/components/TaskList/Content.vue';

export default {
  name: 'Tacalboard',
  components: {
    Sidebar, Content,
  },
};
</script>

<style lang="scss" scoped>
#body {
  background-color: #ffffff;
}
</style>
