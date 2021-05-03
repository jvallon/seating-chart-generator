<template>
  <div>
    <b-input-group size="lg">
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
    <!-- <b-container class="list-item-row">
      <b-row>
        <b-col cols="1">
          <button @click="onDeleteClick">X</button>
        </b-col>
        <b-col cols="11">
          <input
            v-model="student.name"
            placeholder="Enter Student Name"
            @input="onInput">
        </b-col>
      </b-row>
    </b-container> -->
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

<style lang="css">

</style>
