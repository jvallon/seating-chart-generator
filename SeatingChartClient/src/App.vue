<template>
  <div id="app">
    <!-- <b-container> -->
      <b-row cols="lg">
          <StudentList class="col-4 student-list"/>
        <desk-grid class="col-8 desk-grid" :rows="8" :cols="16"></desk-grid>
      </b-row>
    <!-- </b-container> -->
    <!-- <router-view/> -->
  </div>
</template>

<script>
import StudentList from '@/components/Students/StudentList';
import DeskGrid from '@/components/Desks/DeskGrid';

export default {
  name: 'App',
  components: {
    StudentList,
    DeskGrid,
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

.student-list {
  min-width: 200px;
  max-width: 400px;
}

.desk-grid {
  min-width: 600px;
}
</style>
