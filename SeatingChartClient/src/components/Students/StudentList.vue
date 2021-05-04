/* eslint-disable no-console */
<template>
  <div>
    <b-container class="list-container">
      <b-row cols="3">
          <StudentItem class="student-item"
            v-for="student in students"
            :key="student.id"
            :student="student"
            @input="onInput"
            @delete="onDeleteClick"/>
      </b-row>
      <b-row>
        <b-button
          @click="addNewStudent({id: getNewId(), name: ''})">Add new student</b-button>
      </b-row>
    </b-container>
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
    onInput() {
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

/* .list-container {
  max-width: 90vw;
} */

.student-item {
  padding: 4px;
}

</style>
