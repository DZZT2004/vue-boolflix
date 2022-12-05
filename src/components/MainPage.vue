<template>
  <div class="contenitore">
    <HeaderPage @passaDati="setDati"/>
    <div class="cards">
      <CardPage
        v-for="serie in arraySerie"
        :key="serie.id"
        :Titolo="serie.title"
        :TitoloOriginale="serie.original_title"
        :lingua="serie.original_language"
        :Poster="serie.poster_path"
        :Voto="serie.vote_average"
        :Overview="serie.overview"
      />
    </div>

  </div>
</template>
  
<script>
import CardPage from './Card.vue'
import HeaderPage from './HeaderPage.vue'

export default {
   name: 'MainPage',
   components:{
    CardPage,
    HeaderPage,
   },
   data() {
       return {
          arraySerie: [],
       }
   },
   methods:{
    setDati(dati){
        this.arraySerie = dati;
    }
   }
}
</script>
  
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.cards{
    margin-top: 50px;
    display: flex;
    flex-wrap: wrap;
    gap: 50px;
    justify-content: center;
}
.contenitore{
    background-color: grey;
    min-height: 1920px;
}
</style>