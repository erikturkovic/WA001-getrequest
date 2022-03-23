<template>
  <div class="home">
    <ul>
      <li v-for="commit in commits" v-bind:key="commit.sha">
        Commit ->
        <router-link :to="'/commit/' + commit.sha">{{
          commit.sha
        }}</router-link>
      </li>
    </ul>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: "HomeView",
  data: function () {
    return {
      commits: [],
    };
  },
  async mounted() {
    let rezultat = await fetch(
      "https://api.github.com/repos/vuejs/vue/commits"
    );

    let podaci = await rezultat.json();

    console.log(podaci);

    this.commits = podaci;
  },
};
</script>
