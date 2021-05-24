<template>
  <div>
    <b-container id="grid-modifier">
      <b-row>
        <b-col>
          <b-input-group>
            <label>Rows</label>
            <b-form-spinbutton v-model="rows" min="6" max="20"></b-form-spinbutton>
          </b-input-group>
        </b-col>
        <b-col>
          <b-input-group>
            <label>Columns</label>
            <b-form-spinbutton v-model="cols" min="6" max="20"></b-form-spinbutton>
          </b-input-group>
        </b-col>
      </b-row>
    </b-container>

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
    <DeskCard :startPos="{ x:'0', y:'0' }"></DeskCard>
    <label>Active desks: {{ activeDesks }}</label>
  </div>
</template>

<script>
import DeskGridCell from '@/components/Desks/DeskGridCell';
import DeskCard from '@/components/Desks/DeskCard';

export default {
  name: 'DeskGrid',
  components: {
    DeskGridCell,
    DeskCard,
  },
  data() {
    return {
      grid: [{
        id: Number,
        isActive: Boolean,
      }],
      rows: 8,
      rowsMax: 20,
      cols: 12,
      colsMax: 20,
    };
  },
  methods: {
    onGridCellClick(event) {
      const el = event.target;
      this.grid[el.id].isActive = !this.grid[el.id].isActive;
    },
  },
  created() {
    // eslint-disable-next-line prefer-const
    for (let i = 0; i < this.rowsMax * this.colsMax; i += 1) {
      this.grid.push({ id: i, isActive: false });
    }
  },
  computed: {
    visibleGrid() {
      const result = this.grid;
      return result ? result.slice(0, this.rows * this.cols) : [];
    },
    activeDesks() {
      return this.visibleGrid.filter(x => x.isActive === true).length;
    },
  },
};
</script>

<style lang="css" scoped>

#grid-modifier {
  padding: 10px;
}

#grid-modifier label {
  align-content: center;
  padding: 5px;
  margin: 0px;
}

.grid-cell {
  border-width: 1px;
  border-color: grey;
  border-style: solid;
  padding: 0px, 0px;
  /* width: 100%; */
  height: 40px;
}

.grid-cell.active {
  background-color:lightskyblue;
}
</style>
