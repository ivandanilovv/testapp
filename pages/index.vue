<template>
  <main>
    <button @click="getApi('https://archive.org/metadata/TheAdventuresOfTomSawyer_201303')" :disabled="loading">
      Click me!
    </button>
  </main>
</template>

<script>
export default {
  name: 'IndexPage',
  data() {
    return {
      loading: false,
      error: ''
    }
  },
  methods: {
    async getApi(url){
      this.error = ''
      try{
        this.loading = true;
        const data = await this.$axios.$get(url);
        console.log(data)
      } catch (e){
        this.error = 'ERROR! Please try again!'
      } finally {
        this.loading = false;
      }
    }
  },
  mounted() {
    this.getApi('https://www.thecocktaildb.com/api/json/v1/1/search.php?s=margarita')
  }
}
</script>
