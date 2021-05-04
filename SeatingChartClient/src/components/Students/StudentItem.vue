<template>
  <div>
      <b-input-group size="med">
        <b-input-group-prepend>
          <b-button
            variant="danger"
            @click="onDeleteClick">X</b-button>
        </b-input-group-prepend>
        <b-form-input
          placeholder="Enter student name"
          v-model="student.name"
          @input="onInput">
        </b-form-input>
      </b-input-group>
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

<style lang="css" scoped>

</style>
