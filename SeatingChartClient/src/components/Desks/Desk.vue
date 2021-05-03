<template>
  <div>
    <b-card
      :title="student.name">
    </b-card>
  </div>
</template>

<script>
export default {
  name: 'Desk',
  props: {
    student: {
      type: Object,
      required: true,
    },
  },
};
</script>

<style>

</style>
