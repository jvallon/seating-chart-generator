<template>
  <div :id="id" class="grid-cell"
    @click="onGridCellClick"
    :class="[{ active: isActive }]">
  </div>
</template>

<script>
export default {
  name: 'DeskItem',
  props: {
    isActive: {
      type: Boolean,
      required: true,
    },
  },
  methods: {
    onGridCellClick() {
      // const el = event.target;
      this.isActive = !this.isActive;
    },
  },
};
</script>

<style>
.grid-cell {
  border-width: 1px;
  border-color: grey;
  border-style: solid;
  padding: 0px, 0px;
  width: 100%;
  height: 40px;
}

.grid-cell .active {
  background-color:lightskyblue;
}

</style>
