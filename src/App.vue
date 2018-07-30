<template>
  <div>
    <h1>Election day!</h1>
    <button @click="voteForRed">Vote for 🔴</button>
    <button @click="voteForBlue">Vote for 🔵</button>

    <h2>Results</h2>
    <results :red="red" :blue="blue" />
    <total-votes :total="red + blue" />
  </div>
</template>

<script>
const TotalVotes = {
  props: ['total'],
  render (h) {
    return h('div', `Total votes: ${this.total}`)
  },
}

const Results = {
  props: ['red', 'blue'],
  render (h) {
    return h('div', `Red: ${this.red} - Blue: ${this.blue}`)
  },
}

export default {
  components: { TotalVotes, Results },
  data: () => ({ red: 0, blue: 0 }),
  methods: {
    voteForRed () { this.red++ },
    voteForBlue () { this.blue++ },
  },
}
</script>
