<template>
  <div class="colour-picker">
    <div
      v-for="(colour, index) in colours"
      :key="index"
      :style="{ backgroundColor: colour }"
      class="colour-picker__colour"
      @click="setColour(colour)"
    ></div>
  </div>
</template>

<script>
export default {
  name: "ColourPicker",
  props: {
    colours: {
      type: Array
    }
  },
  methods: {
    setColour(colour) {
      this.$emit("update:colour", colour);
    }
  }
};
</script>

<style scoped>
.colour-picker__colour {
  width: 60px;
  height: 120px;
  cursor: pointer;
}

.colour-picker__colour:first-child {
  border-top-left-radius: 20px;
  border-top-right-radius: 20px;
}

.colour-picker__colour:last-child {
  border-bottom-left-radius: 20px;
  border-bottom-right-radius: 20px;
}
</style>