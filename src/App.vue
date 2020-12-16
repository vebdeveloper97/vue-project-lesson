<template>
  <div id="app">
      <h1>{{ carName }}</h1>
      <app-car
        :carName="carName"
        :carYear="carYear"
        @nameChanged="carName = $event"
      ></app-car>
  </div>
</template>

<script>

import Car from "./components/Car";

export default {
  name: 'App',
  components: {
    appCar: Car
  },
  data() {
    return {
      carName: 'Ford',
      carYear: 2019
    }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
