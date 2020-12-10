<template>
  <div id="sidebar">
    <div id="credentials_holder">
      <img :src="avatar">
      <div>{{ credentials }}</div>
    </div>
    <hr>
    <Button text="Planer tygodnia" :img="iconDateRange" :disabled="true" />
    <Button text="Skrzynka odbiorcza" :img="iconInbox" />
    <hr>
    <div id="itemHolder">
      <Button v-for="item in projects" :key="item.uuid" :text="item.name" :img="item.icon" />
    </div>
    <div id="footer">
      <hr>
      <Button text="Nowy projekt" :img="iconNewProject" />
    </div>
  </div>
</template>

<script>
import avatar from '@/assets/avatar.png';
import axios from 'axios';
import Button from '@/components/TaskList/Button.vue';

const api = 'http://127.0.0.1:8080/organizer';

export default {
  name: 'Sidebar',
  components: {
    Button,
  },
  data() {
    return {
      avatar,
      credentials: 'Błażej Hanzel',
      iconDateRange: 'date_range',
      iconInbox: 'inbox',
      iconNewProject: 'create_new_folder',
      projects: [],
    };
  },
  methods: {
    getProjects() {
      axios.get(`${api}/projects`).then((response) => {
        this.projects = response.data;
      });
    },
  },
  beforeMount() {
    this.getProjects();
  },
};
</script>

<style lang="scss" scoped>
#credentials_holder {
  align-content: center;
  height: 75px;
}

#credentials_holder img {
  float: left;
  height: 75px;
  width: 75px;
}

#credentials_holder div {
  align-items: center;
  color: black;
  display: flex;
  float: right;
  font-size: 18px;
  font-weight: bold;
  height: 75px;
  justify-content: center;
  margin: 0px;
  width: 175px;
}

#footer {
  background-color: #efefef;
  bottom: 0px;
  left: 0px;
  padding: 0px 10px 10px 10px;
  position: fixed;
  width: 250px;
}

hr {
  color: #dfdfdf;
  padding: 0 0 0 0;
}

#itemHolder {
  height: calc(100vh - 250px);
  overflow-x: hidden;
  overflow-y: auto;
}

#sidebar {
  background-color: #efefef;
  float: left;
  font-family: sans-serif;
  min-height: calc(100vh - 20px);
  max-width: 250px;
  padding: 10px 10px 10px 10px;
  width: 250px;
}

#sidebar > ul {
  list-style-type: none;
  margin: 0px;
  padding: 0px;
}
</style>
