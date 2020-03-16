<template>
  <div>
    <svg width="200" height="200">
      <polygon :points="points" />
      <circle cx="100" cy="100" r="90" />
    </svg>
    <label>Sides: {{ sides }}</label>
    <input type="range" min="3" max="500" v-model.number="sides" />
    <label>Minimum radius: {{ minRadius }}</label>
    <input type="range" min="0" max="90" v-model.number="minRadius" />
    <label>Update Interval: {{ updateInterval }} milliseconds</label>
    <input type="range" min="10" max="2000" v-model.number="updateInterval" />
  </div>
</template>

<script>
export default {
  data: function() {
    var defaultSides = 10;
    var stats = Array.apply(null, { length: defaultSides }).map(function() {
      return 100;
    });
    return {
      stats: stats,
      points: generatePoints(stats),
      sides: defaultSides,
      minRadius: 50,
      interval: null,
      updateInterval: 500
    };
  },
  watch: {
    sides: function (newSides, oldSides) {
      var sidesDifference = newSides - oldSides
      if (sidesDifference > 0) {
        for (let i = 1; i <= sidesDifference; i++) {
          this.stats.push(this.newRandomValue())
        }
      } else {
        var absoluteSidesDifference = Math.abs(sidesDifference)
        for (let i = 1; i <= absoluteSidesDifference; i++) {
          this.stats.shift()
        }
      }
    },
    stats: function(newStats) {
      TweenLite.to(
        this.$data,
        this.updateInterval / 1000,
        {
          points: generatePoints(newStats),
          ease: Power0.easeNone
        }
      )
    },
    updateInterval: function() {
      this.resetInterval()
    }
  },
  mounted() {
    this.resetInterval()
  }
};
</script>