<template>
  <div class="about">
    {{sha}}
      <li v-for="commit in commits" v-if="commit.sha == sha" v-bind:key="commit.sha">
        
        Ime -> {{commit.author.login}}
      </li>
            <li v-for="commit in commits" v-if="commit.sha == sha" v-bind:key="commit.sha">
        E-mail -> {{commit.commit.author.email}}
      </li>
                  <li v-for="commit in commits" v-if="commit.sha == sha" v-bind:key="commit.sha">
        E-mail -> {{commit.commit.message}}
      </li>
                        <li v-for="commit in commits" v-if="commit.sha == sha" v-bind:key="commit.sha">
        E-mail -> {{commit.commit.author.date}}
      </li>
      
  </div>
</template>





<script>
export default {
props:["sha"],
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

