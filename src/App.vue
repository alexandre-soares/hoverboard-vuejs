<template>
  <div>
    <div class="settings" :class="isNavOpen ? 'open' : 'close'">
      <h1>Settings</h1>
      <h2>Colors</h2>
      <p>Add more colours</p>
      <div class="square-container">
        <span
          class="square-color"
          :style="'background-color: ' + color"
          v-for="(color, index) in colors"
          :key="index"
          @click="removeColor(color)"
        >
        </span>
      </div>
      <div class="add-color">
        <input v-model="color" type="color" name="color" class="color-input" />
        <button @click.prevent="addColor"><i class="fas fa-plus"></i></button>
      </div>
      <h2>Squares</h2>
      <p>Change the number of squares</p>
      <input
        type="number"
        name="number"
        min="10"
        max="1000"
        class="input"
        v-model="squares"
      />
    </div>
    <Home :squares="+squares" :colors="colors" />
    <div class="icon" @click="isNavOpen = !isNavOpen">
      <i class="fas fa-cogs"></i>
    </div>
  </div>
</template>

<script>
import Home from "./components/Home.vue";

export default {
  name: "App",
  data() {
    return {
      squares: 810,
      isNavOpen: false,
      colors: ["#e74c3c", "#8e44ad", "#3498db", "#e67e22", "#2ecc71"],
      color: null
    };
  },
  components: {
    Home
  },
  methods: {
    addColor() {
      this.colors.push(this.color);
    },
    removeColor(color) {
      for (let index = 0; index < this.colors.length; index++) {
        if (color === this.colors[index]) {
          this.colors.splice(index, 1);
        }
      }
    }
  }
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap");

#app {
  width: 100vw;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

* {
  box-sizing: border-box;
}

html {
  font-size: 62.5%;
}

body {
  font-family: "Roboto", sans-serif;
  text-align: center;
  margin: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100vh;
  overflow: hidden;
  background: #111;
}

.fa-cogs {
  position: absolute;
  top: 2rem;
  right: 2rem;
  font-size: 2.5rem;
  cursor: pointer;
  color: lightgray;
}
.settings {
  height: 100vh;
  width: 30rem;
  transform: translateX(-150%);
  position: absolute;
  top: 0;
  left: 0;
  z-index: 999;
  background-color: lightgray;
  transition: 0.3s ease-in-out;
}

.settings.close {
  transform: translateX(-150%);
}

.settings.open {
  transform: translateX(0);
}

.settings input {
  padding: 1rem;
  text-align: center;
  border-radius: 0.5rem;
  border: none;
  color: #8e44ad;
  font-size: 2rem;
}

.settings input:focus {
  outline: 1px solid #8e44ad;
}

.square-container {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
}

.square-color {
  height: 4rem;
  width: 4rem;
  display: inline-block;
  margin: 1rem;
}

.add-color {
  display: flex;
  justify-content: center;
  align-items: center;
}

.color-input {
  border: none;
  height: 5rem !important;
  width: 5rem !important;
}

.add-color button {
  margin-left: 2rem;
}

.add-color .fa-plus {
  background-color: transparent;
  border: none;
}
</style>
