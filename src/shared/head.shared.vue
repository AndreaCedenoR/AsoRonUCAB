<template>
  <header class="app-header">
      <button class="close-button" @click="cerrar">x</button>
      <h1 class="app-title">ASORONUCAB</h1>
  </header>
</template>

<script>
  export default {
  methods: {
      cerrar() {

      }
  }
  }
</script>

<style>


.app-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px;
  background-color: #333;
  color: white;
  max-height: 500px;
  top: 0;
  max-height: 100px;
}

.close-button {
  background-color: transparent;
  border: none;
  color: white;
  font-size: 1.5rem;
  cursor: pointer;
}

.app-title {
      text-align: center;
      margin: auto;
}
</style>
