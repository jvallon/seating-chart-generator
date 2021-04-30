<template>
  <div id="app">
    <student-list/>
    <router-view/>
  </div>
</template>

<script>
import StudentList from '@/components/Students/StudentList';

export default {
  name: 'App',
  components: {
    StudentList,
  },
  data() {
    return {
    };
  },
};
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
