<template>
  <div class="home">
    <ul>
      <li v-for="item in commits" v-bind:key="item.sha">
        Commit ->  <a href="/about">{{item.sha}}</a>
      </li>
      </ul>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from "@/components/HelloWorld.vue";
import ShowCommits from "@/components/ShowCommits.vue";

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
