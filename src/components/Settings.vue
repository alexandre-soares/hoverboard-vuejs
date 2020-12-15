<template>
  <div class="settings"></div>
</template>

<script>
export default {};
</script>

<style>
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

.settings.open {
  transform: translateX(0);
}
</style>
