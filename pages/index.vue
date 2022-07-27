<template>
  <main>
    <button @click="getApi" :disabled="loading">
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
    async getApi(){
      this.error = ''
      try{
        this.loading = true;
        const data = await this.$axios.$get('/metadata/TheAdventuresOfTomSawyer_201303');
        console.log(data)
      } catch (e){
        this.error = 'ERROR! Please try again!'
      } finally {
        this.loading = false;
      }
    }
  }
}
</script>
