<template>
  <Moveable id="desk-container"
    class="moveable"
    v-bind="moveable"
    @drag="handleDrag"
    @drag-end="dragEnd"
    :style="{ transform: this.transform }">
    <span>Desk Card</span>
  </Moveable>
</template>

<script>
import Moveable from 'vue-moveable';

export default {
  name: 'DeskCard',
  components: {
    Moveable,
  },
  props: {
    startPos: {
      x: { type: Number },
      y: { type: Number },
    },
  },
  data() {
    return {
      moveable: {
        draggable: true,
        throttleDrag: 1,
        bounds: {
          left: 0, right: 800, top: 400, bottom: 750,
        },
        resizable: false,
        throttleResize: 1,
        keepRatio: false,
        scalable: false,
        throttleScale: 0,
        rotatable: false,
        throttleRotate: 0,
        pinchable: false, // ["draggable", "resizable", "scalable", "rotatable"]
        origin: false,
        snappable: true,
      },
      transform: '',
      position: {
        x: 0,
        y: 0,
      },
    };
  },
  methods: {
    handleDrag({ transform }) {
      this.transform = transform;
    },
    dragEnd({ clientX, clientY }) {
      this.position = { x: clientX, y: clientY };
    },
  },
  watch: {
    startPos: () => {
      this.position.x = this.startPos.x;
      this.position.y = this.startPos.y;
      this.transform = `translate(${this.startPos.x}, ${this.startPos.y})`;
    },
    transform: () => {
      // eslint-disable-next-line no-console
      // console.log(this.transform);
    },
  },
};
</script>

<style>

</style>
