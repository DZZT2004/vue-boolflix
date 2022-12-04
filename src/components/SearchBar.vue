<template>
    <div class="searchbar">
    <label for="st">
      <input
        type="text"
        id="s"
        v-model="stringa"
        name="st"
        @keyup.enter="search"
       >
    </label>
    </div>
  </template>
  
<script>
export default {
   name: 'SearchBar',
   data() {
       return {
          stringa: '',
       }
   },
   methods: {
       search() {
           this.$emit('search', this.stringa)
       }
   }
}
</script>
  
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  
</style>