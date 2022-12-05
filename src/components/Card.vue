<template>
  <div class="card">
    <img :src="isx" alt="errore">
    <div class="info">
        <h4>Titolo:</h4> <span></span>
        <h4>Titolo Originale:</h4> <span></span>
        <h4>Voto:</h4> <span></span>
        <h4>Overview:</h4> <span></span>
    </div>
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
   computed: {
    image(){
      let appoggio = 'background-image: url('+'http://image.tmdb.org/t/p/w342'+ this.Poster+')';
      return appoggio;
    }
   }
}
</script>
  
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.card{
    width: 300px;
    height: 450px;
    .info{
        width: 300px;
        height: 450px;
        background-color: black;
        width: 100%;
        display: none;
        padding: 50px 10px 50px;
        box-sizing: border-box;
        text-align: left;
    }
}
.card:hover{
  img{
    display: none;
  }
  .info{
    display: block;
  }
}
</style>