<template>
  <div class="container" id="container">
    <h1>HOVERBOARD</h1>
    <div
      class="square"
      v-for="i in squares"
      :key="i.index"
      @mouseenter="setColor"
      @mouseout="removeColor"
    ></div>
  </div>
</template>

<script>
export default {
  name: "Home",
  data() {},
  props: {
    squares: {
      type: Number,
      default: 810
    },
    colors: {
      type: Array,
      default: null
    }
  },
  mounted() {
    this.createGrid();
  },
  methods: {
    createGrid() {
      for (let i = 0; i < this.squares; i++) {
        const container = document.getElementById("container");
        const square = document.createElement("div");

        square.classList.add("square");

        // square.addEventListener('mouseover', () => setColor(square))
        // square.addEventListener('mouseout', () => removeColor(square))

        container.appendChild(square);
      }
    },
    setColor(event) {
      const element = event.target;
      const color = this.getRandomColor();
      element.style.background = color;
      element.style.boxShadow = `0 0 2px ${color}, 0 0 1rem ${color}`;
    },
    removeColor(event) {
      const element = event.target;
      element.style.background = "#474747";
      element.style.boxShadow = "0 0 2px #000";
    },
    getRandomColor() {
      return this.colors[Math.floor(Math.random() * this.colors.length)];
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.container {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-wrap: wrap;
  max-width: 60rem;
}

h1 {
  display: block;
  text-align: center;
  color: #aaa;
  width: 100%;
  letter-spacing: 3px;
  font-weight: 100;
  font-size: 3.2rem;
}

.square {
  background-color: #474747;
  box-shadow: 0 0 2px #000;
  height: 1.6rem;
  width: 1.6rem;
  margin: 2px;
  transition: 2s ease;
}

.square:hover {
  transition-duration: 0s;
}
</style>
