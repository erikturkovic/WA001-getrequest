<template>
  <div class="home">

  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import ShowCommits from '@/components/ShowCommits.vue'

export default {
  name: 'HomeView',
  async mounted(){

    let rezultat = await fetch("https://api.github.com/repos/vuejs/vue/commits");

    let podaci = await rezultat.json()

    console.log(podaci);

  },
};
</script>
