<template>
  <div>
    <h1>Election day!</h1>
    <button @click="voteForRed">Vote for 🔴</button>
    <button @click="voteForBlue">Vote for 🔵</button>

    <h2>Results</h2>
    <results/>
    <total-votes/>
  </div>
</template>

<script>
import Vue from 'vue'

const state = new Vue({
  data () {
    return {
      red: 0,
      blue: 0,
    }
  },
  methods: {
    voteForRed () { this.red++ },
    voteForBlue () { this.blue++ },
  },
})

const TotalVotes = {
  render: h => h('div', `Total votes: ${state.red + state.blue}`),
}

const Results = {
  render: h => h('div', `Red: ${state.red} - Blue: ${state.blue}`),
}

export default {
  components: { TotalVotes, Results },
  methods: {
    voteForRed () { state.voteForRed() },
    voteForBlue () { state.voteForBlue() },
  },
}
</script>
