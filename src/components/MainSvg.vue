<template>
  <div class="hello">
    <p>Hello to SVG</p>
    <div>
      <svg>
        <rect class="rect" x="10" y="20" width="150" height="100" />
      </svg>
      <svg>
        <circle class="circle" cx="60" cy="60" r="50" />
      </svg>
    </div>
    <div id="set">
      <div>
        x:
        <input v-model.number="x" :max="maxX" min="0" type="range" />
        y:
        <input v-model.number="y" :max="maxY" min="0" type="range" />
        width:
        <input v-model.number="width" :max="maxWidth" min="10" type="range" />
        height:
        <input v-model.number="height" :max="maxHeight" min="10" type="range" />
      </div>
      <svg :width="svgWidth" :height="svgHeight">
        <rect class="rect" :x="x" :y="y" :width="width" :height="height" />
      </svg>
    </div>
    <SvgShapes v-if="false" />
    <!-- <PolygonAnime /> -->
  </div>
</template>

<script>
import SvgShapes from './SvgShapes'
// import PolygonAnime from './PolygonAnime'

export default {
  name: "MainSvg",
  components: {
    SvgShapes,
    // PolygonAnime
  },
  data() {
    return {
      x: 10,
      y: 20,
      width: 150,
      height: 100,
      svgWidth: 300,
      svgHeight: 300
    };
  },
  computed: {
    maxX() {
      return this.svgWidth - this.width;
    },
    maxY() {
      return this.svgHeight - this.height;
    },
    maxWidth() {
      return this.svgWidth - this.x;
    },
    maxHeight() {
      return this.svgHeight - this.y;
    }
  }
};
</script>

<style lang="scss" scoped>
.rect {
  fill: red;
}
.circle {
  fill: orange;
  stroke: midnightblue;
  stroke-width: 5;
}
</style>
