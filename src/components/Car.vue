<template>
  <div class="car">
    <h1>{{ counter }}</h1>
    <h2>CarName: {{ carNameNew }} | {{ reverseName }}</h2>
    <h3>CarYear: {{ carYearNew }}</h3>
    <button @click="changeName">Change Name</button>
    <button @click="counterUpdate()">Add Counter</button>
  </div>
</template>

<script>
import {EventEmitter} from './../main'

export default {
  name: "Car",
  props: {
    nameChanged: {
      type: Function
    },
    carName: {
      type: String,
      required: true
    },
    carYear: {
      type: Number,
      required: true
    }
  },
  data(){
    return {
      carNameNew: this.carName,
      carYearNew: this.carYear,
      counter: 0,
    }
  },
  created() {
    EventEmitter.$on('counterUpdate', (num) => {
      this.counter + num
    })
  },
  methods: {
    changeName: function (){
      this.carNameNew = 'Mazda'
      this.$emit('nameChanged', this.carNameNew)
    },

  },
  computed: {
    reverseName: function (){
      return this.carName.split('').reverse().join('')
    }
  }
}
</script>

<style scoped>

</style>