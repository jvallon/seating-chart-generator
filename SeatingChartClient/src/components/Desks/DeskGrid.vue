<template>
  <div>
    <b-container id="desk-grid" class="desk-grid">
      <b-row no-gutters v-for="(row, rowIdx) in rows" :key="rowIdx" align-h="start">
        <b-col no-gutters v-for="(col, colIdx) in cols" :key="colIdx">
          <div :id="(rowIdx*cols) + colIdx" class="grid-cell"
            @click="onGridCellClick"
            :class="{ active: grid[(rowIdx*cols) + colIdx].isActive }">
          </div>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
import DeskGridCell from '@/components/Desks/DeskGridCell';

export default {
  name: 'DeskGrid',
  props: ['rows', 'cols'],
  components: {
    DeskGridCell,
  },
  data() {
    return {
      grid: [{
        id: Number,
        isActive: Boolean,
      }],
    };
  },
  methods: {
    onGridCellClick(event) {
      const el = event.target;
      this.grid[el.id].isActive = !this.grid[el.id].isActive;
    },
  },
  mounted() {
    // eslint-disable-next-line prefer-const
    for (let i = 0; i < this.rows * this.cols; i += 1) {
      this.grid.push({ id: i, isActive: false });
    }
  },
  computed: {
  },
};
</script>

<style lang="css" scoped>

.col {
  /* border-width: 1px;
  border-color: grey;
  border-style: solid; */
}

.grid-cell {
  border-width: 1px;
  border-color: grey;
  border-style: solid;
  padding: 0px, 0px;
  width: 100%;
  height: 40px;
  /* height: 40px;
  width: 40px; */
}

.grid-cell.active {
  background-color:lightskyblue;
}
</style>
