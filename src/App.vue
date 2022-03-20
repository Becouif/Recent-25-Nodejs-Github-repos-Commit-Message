<template>
  <div>
    <the-header></the-header>
    <commit-github-vue></commit-github-vue>
  </div>
</template>

<script>
import TheHeader from "./components/TheHeader.vue"
import CommitGithubVue from "./components/CommitGithub.vue"
export default {
  components: {CommitGithubVue, TheHeader},
 
}
</script>