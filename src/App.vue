<template>
  <div id="app">
    <p>Enter your username to get some Github stats!</p>
    <form v-on:submit.prevent>
      <input type="text" v-model="username" placeholder="Enter a github username here" name="username" />
      <button @click="onSubmit">Go!</button>
    </form>
    <github-output></github-output>
  </div>
</template>

<script>
import bus from './bus'
import Vue from 'vue'
import GithubOutput from './GithubOutput.vue'

export default {
  name: 'app',
  components: {
    'github-output': GithubOutput,
  },
  methods: {
    onSubmit(event) {
      if (this.username && this.username !== '') {
        bus.$emit('new-username', this.username)
        const url = `https://api.github.com/users/${this.username}`
        fetch(url).then(r => r.json()).then(data => {
          Vue.set(this.githubData, name, data)
        })
      }
    },
  },
  data () {
    return {
      username: '',
      currentUsername: null,
      githubData: {}
    }
  }
}
</script>

<style>
</style>
