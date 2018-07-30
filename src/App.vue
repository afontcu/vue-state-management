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
const state = {
  red: 0,
  blue: 0,
}

const TotalVotes = {
  data () { return state },
  render (h) {
    return h('div', `Total votes: ${this.red + this.blue}`)
  },
}

const Results = {
  data () { return state },
  render (h) {
    return h('div', `Red: ${this.red} - Blue: ${this.blue}`)
  },
}

export default {
  components: { TotalVotes, Results },
  data () { return state },
  methods: {
    voteForRed () { this.red++ },
    voteForBlue () { this.blue++ },
  },
}
</script>
