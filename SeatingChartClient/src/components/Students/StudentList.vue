/* eslint-disable no-console */
<template>
  <div class="listContainer">
    <StudentItem
      v-for="student in students"
      :key="student.id"
      :student="student"
      @input="onInput"
      @delete="onDeleteClick"/>

    <b-button
      @click="addNewStudent({id: getNewId(), name: ''})">Add new student</b-button>

    <!-- <li
      v-for="student in students"
      :key="student.id">
      <textblock>{{ student.name }}</textblock>
    </li> -->
  </div>
</template>

<script>
import StudentItem from './StudentItem';

export default {
  name: 'StudentList',
  components: { StudentItem },
  data() {
    return {
      fields: ['name'],
      students: [
        {
          id: 1, name: 'josh',
        },
        {
          id: 2, name: 'devon',
        },
      ],
    };
  },
  methods: {
    onInput(student) {
      // TODO update db
    },
    addNewStudent(student) {
      this.students.push(student);
      // TODO add new db entry
    },
    onDeleteClick(id) {
      const pos = this.students.findIndex(x => x.id === id);
      if (pos >= 0) {
        this.students.splice(pos, 1);
        // TODO delete from db
      }
    },
    getNewId() {
      if (this.studentCount === 0) {
        return 1;
      }

      let maxId = 0;
      this.students.forEach((obj) => {
        if (obj.id > maxId) {
          maxId = obj.id;
        }
      });
      return maxId + 1;
    },
  },
  computed: {
    studentCount() {
      return this.students.length;
    },
  },
};
</script>

<style lang="css">

.listContainer {
  flex-basis: auto;
  max-width: 30vw;
}
</style>
