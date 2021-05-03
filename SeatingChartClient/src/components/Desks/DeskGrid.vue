<template>
  <div>
    <!-- <b-container id="desk-grid" class="desk-grid"> -->
      <!-- <div v-for="cell in rows*cols" :key="cell">
        <b-checkbox></b-checkbox>
      </div> -->
      <b-row class="desk-grid-row" v-for="row in rows" :key="row">
        <div class="desk-grid-col" v-for="col in cols" :key="col">
          <div class="grid-cell">
            <b-checkbox></b-checkbox>
          </div>
        </div>
      </b-row>
    <!-- </b-container> -->
  </div>
</template>

<script>
import Desk from '@/components/Desks/Desk';

export default {
  name: 'DeskGrid',
  props: ['rows', 'cols'],
  components: {
    Desk,
  },
};
</script>

<style lang="css" scoped>
#desk-grid {
  /* border-width: .5px; */
}

.grid-cell {
  border-width: 1px;
  border-color: grey;
  border-style: solid;
  padding: 0;
  margin: 0;
  min-height: 1fr;
  min-width: 1fr;
}
</style>
