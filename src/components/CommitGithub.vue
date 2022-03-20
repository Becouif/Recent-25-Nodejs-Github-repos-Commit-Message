<template>
  <div v-for="commit in commits" :key="commit.id">
    <base-card>
      <p>{{ commit.message }}</p>
    </base-card>
  </div>
</template>

<script>
import BaseCard from "./BaseCard.vue";
export default {
  components: { BaseCard },
  data() {
    return {
      commits: [],
    };
  },
  methods: {
    loadCommit() {
      const results = [];
      fetch("https://api.github.com/repos/nodejs/node/commits")
        .then((res) => {
          if (res.ok) {
            return res.json();
          }
        })
        .then((data) => {
          for (let i = 0; i < 25; i++) {
            results.push({
              id: i,
              message: data[i].commit.message,
            });
            this.commits = results;
          }
        });
    },
  },
  mounted(){
      this.loadCommit();
  }
};
</script>
