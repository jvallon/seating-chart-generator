<template>
  <div>
    <!-- <b-row> -->
      <button @click="onDeleteClick">X</button>
      <input v-model="student.name" placeholder="Enter Student Name" @input="onInput">
    <!-- </b-row> -->
  </div>
</template>

<script>
export default {
  name: 'StudentItem',
  props: {
    student: {
      type: Object,
      required: true,
    },
  },
  methods: {
    onDeleteClick() {
      this.$emit('delete', this.student.id);
    },
    onInput() {
      this.$emit('input', this.student);
    },
  },
};
</script>

<style scoped>
.button {
  width: 5px;
}
</style>
