<template>
  <div class="card" v-bind:style="image">
    {{stampa()}}
  </div>
</template>
  
<script>
export default {
   name: 'CardPage',
   data() {
       return {
          isx: 'http://image.tmdb.org/t/p/w300'+ this.Poster
       }
   },
   props: {
     Titolo: String,
     TitoloOriginale: String,
     Lingua: String,
     Voto: Number,
     Poster: String,
   },
   methods: {
    stampa(){
        console.log(this.image)
    }
   },
   computed: {
    image(){
      let appoggio = 'background-image: url('+'http://image.tmdb.org/t/p/w300'+ this.Poster+')';
      return appoggio;
    }
   }
}
</script>
  
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.card{
    width: 300px;
    height: 400px;
}
</style>