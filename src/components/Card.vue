<template>
  <div class="card">
    <img :src="isx" alt="errore">
    <div class="info">
        <h4>Titolo:</h4> <span>{{Titolo}}</span>
        <h4>Titolo Originale:</h4> <span>{{TitoloOriginale}}</span>
        <h4>Voto:</h4> <span><font-awesome-icon icon="fa-solid fa-star" class="stella" v-for="n in punteggio" :key="n.id"/></span>
        <h4>Overview:</h4> <span>{{Overview}}</span>
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
     Overview: String
   },
   computed: {
    image(){
      let appoggio = 'background-image: url('+'http://image.tmdb.org/t/p/w342'+ this.Poster+')';
      return appoggio;
    },
    punteggio(){
      return Math.ceil(this.Voto/2);
    }
   }
}
</script>
  
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.card{
    width: 350px;
    height: 550px;
    .info{
        width: 300px;
        max-height: 600px;
        height: 550px;
        background-color: black;
        width: 100%;
        display: none;
        padding: 10px 10px 50px;
        box-sizing: border-box;
        text-align: left;
        border: 2px solid white;
    }
}
.card:hover{
  img{
    display: none;
  }
  .info{
    display: block;
    h4{
      margin-top: 10px;
      margin-bottom: 10px;
    }
  }
}
.stella{
  color: yellow;
}
</style>