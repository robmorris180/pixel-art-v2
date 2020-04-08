<template>
  <div id="app">
    <Header :colour="currentColour" />
    <ColourPicker :colours="colours" @update:colour="setColour" />
    <ColourGrid :colour="currentColour" />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import ColourPicker from "./components/ColourPicker.vue";
import ColourGrid from "./components/ColourGrid.vue";

export default {
  name: "App",
  components: {
    Header,
    ColourPicker,
    ColourGrid
  },
  data() {
    return {
      colours: ["#3ea6aa", "#e8a093", "#e4bb58", "#fff", "#165070"],
      currentColour: "#3ea6aa"
    };
  },
  methods: {
    setColour(colour) {
      this.currentColour = colour;
    }
  }
};
</script>

<style>
* {
  box-sizing: border-box;
}

body {
  background-color: #111;
}

#app {
  font-family: "Open Sans", sans-serif;
  padding: 2rem;
  display: grid;
  grid-template-columns: 60px 1fr;
  grid-template-rows: 100px 1fr;
  grid-gap: 2rem;
  grid-template-areas:
    "header header"
    "sidebar content";
  align-items: center;
  height: 100vh;
}

header {
  grid-area: header;
}

.colour-picker {
  grid-area: sidebar;
}

.colour-grid {
  grid-area: content;
  justify-self: center;
}
</style>
