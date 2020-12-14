<template>
  <div id="app">
    <div class="text-center mb-3">
      <h2>Score</h2>
      {{score}}
    </div>

    <!--  Using Once event modifier  -->
    <div class="mb-3">
      <p>Using vue event modifier Once</p>
      <button  class="btn btn-success"
               @click.once="score++">
        Add 1 using event once
      </button>
    </div>

    <!--  button disable  -->
    <div class="mb-3">
      <p>Using disable modifier in button</p>
      <button  class="btn btn-success"
               :disabled="disable"
               @click="add">
        Add 1 using :disable
      </button>

      <button class="btn btn-warning mx-2" @click="disable = false"> On</button>
    </div>

    <!--  Underscore library   -->
    <div class="mb-3">
      <p>Using throttle function in <a href="https://github.com/HKskn/vue-underscore">underscore</a> library</p>
      <button  class="btn btn-success"
               @click="throttleAdd">
        Add 1 using throttle
      </button>
    </div>
  </div>
</template>

<script>
import _ from 'underscore';
export default {
  name: 'App',
  data() {
    return {
      score: 0,
      disable: false
    }
  },
  methods: {
    add: function () {
      this.disable = true //disable button
      this.score++
    },
    throttleAdd: _.throttle(function () {
      this.score++
    }, 1000, {trailing: false})
  }
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
