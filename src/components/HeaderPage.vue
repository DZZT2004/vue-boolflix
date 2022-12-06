<template>
  <div class="header">
    <h1>BOOLFLIX</h1>
    <SearchBar @search="cerca"/>
  </div>
</template>

<script>
import axios from 'axios'
import SearchBar from './SearchBar.vue'

export default {
  name: 'HeaderPage',
  components: {
    SearchBar
  },
  data() {
       return {
          arrayFilm: [],
          arraySerie: [],
          api: 'https://api.themoviedb.org/3/movie/550?api_key=5ef4365de9d5d00883cfd7cabdb50f7f'
       }
   },
  methods: {
    cerca(stringa){
        axios.get('https://api.themoviedb.org/3/search/movie?api_key=5ef4365de9d5d00883cfd7cabdb50f7f&language=en-US&query='+stringa+'&page=1&include_adult=false')
        .then((axiosResponse) => {
           console.log(axiosResponse);
           this.arrayFilm = axiosResponse.data.results;
           console.log(this.arrayFilm);
           axios.get('https://api.themoviedb.org/3/search/tv?api_key=5ef4365de9d5d00883cfd7cabdb50f7f&language=en-US&query='+stringa+'&page=1&include_adult=false')
          .then((axiosResponse) => {
            console.log(axiosResponse);
            this.arraySerie = axiosResponse.data.results;
            console.log(this.arraySerie);
            this.$emit('passaDati', {
            films: this.arrayFilm,
            series: this.arraySerie
          })
          })
          .catch((error) => {
            console.log(error);
            if (error.response.status === 404
              && error.response.data.error === 'There is nothing here'
            ) {
              this.arraySerie = [];
            }
          });
        })
        .catch((error) => {
           console.log(error);
           if (error.response.status === 404
             && error.response.data.error === 'There is nothing here'
           ) {
             this.arraySerie = [];
           }
        });
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.header{
  background-color: black;
  padding: 20px;
}
h1{
  margin-top: 0;
  color: red;
}
</style>