<template>
  <div id="taskContent">
    <h1>Skrzynka odbiorcza</h1>
    <hr>
    <div id="itemHolder">
      <Task v-for="item in tasks" :key="item.uuid" :task="item" />
    </div>
    <div id="footer">
      <hr>
      <Button text="Nowe zadanie" :img="iconNewTask" />
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import Button from '@/components/TaskList/Button.vue';
import Task from '@/components/TaskList/Task.vue';

const api = 'http://127.0.0.1:8080/organizer';

export default {
  name: 'TaskContent',
  components: {
    Button, Task,
  },
  data() {
    return {
      iconNewTask: 'add_task',
      tasks: [],
    };
  },
  methods: {
    getTasks(project) {
      axios.get(`${api}/tasks?project=${project}`).then((response) => {
        this.tasks = response.data;
      }).catch((error) => {
        if (error.response.status === 400) {
          console.log('Podany projekt nie istnieje!'); // TODO
        }
      });
    },
  },
  beforeMount() {
    this.getTasks('inbox');
  },
};
</script>

<style lang="scss" scoped>
button {
  background-color: #ffffff;
}

#footer {
  background-color: #ffffff;
  bottom: 0px;
  left: 270px;
  padding: 0px 10px 10px 10px;
  position: fixed;
  width: calc(100% - 290px);
}

h1 {
  font-family: sans-serif;
  margin: 0px;
}

#itemHolder {
  height: calc(100vh - 127px);
  overflow-x: hidden;
  overflow-y: auto;
}

#taskContent {
  margin-left: 270px;
  padding: 10px 10px 10px 10px;
}
</style>
