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

const createStore = ({ state, mutations }) => {
  return new Vue({
    data () {
      return { state }
    },
    methods: {
      commit (mutationName) {
        mutations[mutationName](this.state)
      },
    },
  })
}

const store = createStore({
  state: { red: 0, blue: 0 },
  mutations: {
    voteForRed (state) { state.red++ },
    voteForBlue (state) { state.blue++ },
  },
})

const TotalVotes = {
  render: h => h('div', `Total votes: ${store.state.red + store.state.blue}`),
}

const Results = {
  render: h => h('div', `Red: ${store.state.red} - Blue: ${store.state.blue}`),
}

export default {
  components: { TotalVotes, Results },
  methods: {
    voteForRed () { store.commit('voteForRed') },
    voteForBlue () { store.commit('voteForBlue') },
  },
}
</script>
