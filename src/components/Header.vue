<template>
  <header>
    <h1>
      Pixel
      <span :style="{ color: colour }">Art</span>
    </h1>
    <div class="current-color"></div>
  </header>
</template>

<script>
export default {
  name: "Header",
  props: {
    colour: String
  }
};
</script>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

h1 {
  display: flex;
  font-family: "Titillium Web", sans-serif;
  color: #367b92;
  text-transform: uppercase;
  font-size: 100px;
  margin: 0;
}

h1 >>> span {
  color: #3ea6aa;
}

.current-color {
  width: 40px;
  height: 40px;
}
</style>