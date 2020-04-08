<template>
  <div class="colour-grid">
    <div
      v-for="(pixel, index) in pixels"
      :key="index"
      :style="{ backgroundColor: pixel.colour }"
      class="colour-grid__item"
      @click="updatePixelColour(index)"
    ></div>
  </div>
</template>

<script>
export default {
  name: "ColourGrid",
  props: {
    colour: String
  },
  data() {
    return {
      pixels: [],
      gridSize: 100
    };
  },
  methods: {
    initGrid() {
      for (let i = 0; i < this.gridSize; i++) {
        this.pixels.push({
          colour: "#fff"
        });
      }
    },
    updatePixelColour(index) {
      this.pixels[index].colour = this.colour;
      this.saveDrawing();
    },
    saveDrawing() {
      const parsed = JSON.stringify(this.pixels);
      localStorage.setItem("pixels", parsed);
    }
  },
  mounted() {
    if (localStorage.getItem("pixels")) {
      try {
        this.pixels = JSON.parse(localStorage.getItem("pixels"));
      } catch (error) {
        localStorage.removeItem("pixels");
      }
    } else {
      this.initGrid();
    }
  }
};
</script>

<style scoped>
.colour-grid {
  display: grid;
  grid-template-columns: repeat(10, 1fr);
  grid-template-rows: repeat(10, 1fr);
  width: 800px;
  height: 800px;
}

.colour-grid__item {
  border-top: 1px dotted #111;
  border-left: 1px dotted #111;
}

.colour-grid__item:nth-child(-n + 10) {
  border-top-color: transparent;
}

.colour-grid__item:nth-child(10n + 1) {
  border-left-color: transparent;
}
</style>