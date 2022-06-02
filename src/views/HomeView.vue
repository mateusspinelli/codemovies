<template>
  <div class="main">
    <form @submit.prevent="SearchMovies()" class="searchBox">
      <input type="text" placeholder="What are you looking for?" class="searchText" v-model="search"/>
      <button type="submit" class="searchButton"></button>
    </form>

    <div class="moviesList">
      <div class="movie" v-for="movie in movies" :key="movie.imdbID">
        <router-link :to="'/movie/' + movie.imdbID" class="movieLink">
          <div class="productImage">
            <img :src="movie.Poster" alt="Movie Poster" />
          </div>
          <div class="movieDetail">
            <h3>{{movie.Title}}</h3>
            <div>
              <p class="year">{{movie.Year}}</p>
              <p class="type">{{ movie.Type }}</p>
            </div>
          </div>
        </router-link>
      </div>
    </div>
  </div>
</template>

<script>
import { ref } from 'vue';
import env from '@/env.js'

export default {
  setup () {
    const search = ref("");
    const movies = ref([]);

    const SearchMovies = () => {
      if (search.value != ""){
        //fetch(`http://www.omdbapi.com/?apikey=${env.apikey}&s=${search.value}&y=1990`)//
        fetch(`http://www.omdbapi.com/?apikey=${env.apikey}&s=${search.value}`)
          .then(response => response.json())
          .then(data => {
            movies.value = data.Search;
            search.value = "";
          });
      }
    }


    return {
      search,
      movies,
      SearchMovies
    }
  }
}
</script>


<style lang="scss">

$branco: #FEFEFE;
$cor1: #CFDBD5;
$cor2: #E8EDDF;
$cor3: #F5CB5C;
$cor4: #242423;
$cor5: #333533;

*{
  list-style: none;
  text-decoration: none;
}

.main{
  background-color: $cor5;
  min-height: 100vh;
  min-width: 80vw;
}

.searchBox{
  display: flex;
  padding: 80px 15vw 80px 15vw;
  margin: 0;
}

.searchText{
  padding: 5px 0px 5px 30px;
  height: 80px;
  width: 45vw;
  font-size: 40px;
  border-radius: 20px;
  border: solid black 1px;
  background-color: $cor1;
}

.searchButton{
  margin-left: -100px;
  background-color: $cor1;
  height: 80px;
  width: 100px;
  border-radius: 0px 20px 20px 0px;
  background-image: url("../img/searchIcon.svg");
  background-repeat: no-repeat;
  background-size: 60px;
  background-position: center;
  border: solid black 1px;
  cursor: pointer;
}








.moviesList{
	display: grid;
	grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
	grid-gap: 20px;
	padding-inline-start: 20px;
	padding-inline-end: 40px;
}


.movie{
  border-radius: 20px;
  border: solid white 1px;
}

.productImage img{
  border-radius: 20px 20px 0px 0px;
  height: 500px;
  width: 350px;
}

.movieDetail h3{
  color: $cor1;
  font-size: 20px;
  padding: 5px 0px 5px 10px;
}

.movieDetail div{
  display: flex;
  justify-content: space-between;
  padding: 10px 10px 10px 10px;
}

.movieDetail p{
  font-size: 15px;
  color: $cor1;
  text-transform: capitalize;
}


</style>