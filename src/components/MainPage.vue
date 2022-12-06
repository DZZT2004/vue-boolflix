<template>
  <div class="contenitore">
    <HeaderPage @passaDati="setDati"/>
    <div class="cards">
      <CardPage
        v-for="film in arrayFilm"
        :key="film.id"
        :Titolo="film.title"
        :TitoloOriginale="film.original_title"
        :Lingua="film.original_language"
        :Poster="film.poster_path"
        :Voto="film.vote_average"
        :Overview="film.overview"
      />
      <CardPage
        v-for="serie in arraySerie"
        :key="serie.id"
        :Titolo="serie.name"
        :TitoloOriginale="serie.name"
        :Lingua="serie.original_language"
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
          arrayFilm: [],
          arraySerie: [],
       }
   },
   methods:{
    setDati({films, series}){
      console.log(films)
      console.log(series)
      this.arrayFilm = films
      this.arraySerie = series
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