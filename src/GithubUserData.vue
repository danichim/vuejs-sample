<template>
	<div v-if="data">
	  <h4>{{ data.name }} - {{data.bio}} </h4>
	  <p>{{ data.created_at }}</h4>
	  <p>Avatar: <img v-bind:src="data.avatar_url" width="80"></p>
	  <p>Link: <a v-bind:href="data.blog" target="_blank"> {{data.blog}} </a></p>
	  <p>{{ data.company }} {{ data.location }}</p>
	  <p></p>
	  <p>Number of repos: {{ data.public_repos }}</p>
	  <p>Number of gists: {{ data.public_gists }}</p>
	</div>
</template>

<script>
export default {
  name: 'GithubUserData',
  props: ['data'],
  data() {
    return {}
  }
}
</script>

<style>
</style>