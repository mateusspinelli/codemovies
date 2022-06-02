<template>
<div class="components">

  <header>
    <div class="headerTitle">
      <router-link to="/" class="link">
        <img src="./img/movieIcon2.svg" alt="">
      </router-link>
      <router-link to="/" class="link">
        <h1>CodeMovies</h1>
      </router-link>
    </div>
    <hr>
    

    <div class="menuTitle">
      <router-link to="/Movies" class="link">
        <img src="./img/movieIcon.svg" alt="">
      </router-link>
      <router-link to="/Movies" class="link">
        <h1>Movies</h1>
      </router-link>
    </div>

    
    <div class="menuTitle">
      <router-link to="/Series" class="link">
        <img src="./img/seriesIcon.svg" alt="">
      </router-link>
      <router-link to="/Series" class="link">
        <h1>Series</h1>
      </router-link>
    </div>


    <div class="menuTitle">
      <router-link to="/Year" class="link">
        <img src="./img/yearIcon.svg" alt="">
      </router-link>
      <router-link to="/Year" class="link">
        <h1>Year</h1>
      </router-link>
    </div>


  </header>


  <main>
    <router-view/>
  </main>
</div>
</template>

<style lang="scss">

$branco: #FEFEFE;
$cor1: #CFDBD5;
$cor2: #E8EDDF;
$cor3: #F5CB5C;
$cor4: #242423;
$cor5: #333533;

@import url('https://fonts.googleapis.com/css2?family=Poiret+One&display=swap');

*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Poiret One', cursive;
}

.components{
    display: flex;
}

header{
  height: auto;
  min-height: 100vh;
  min-width: 20vw;
  width: 20vw;
  background-color: $cor3;
}


.headerTitle{
  display: flex;
}

.link{
  text-decoration: none;
  color: $cor4;
}

.headerTitle img{
  margin: 20px;
  height: 64px;
  width: 64px;
}

.headerTitle h1{
  font-size: 48px;
  color: $cor4;
  padding: 25px 0 0 0;
}

header hr{
  border: solid 1px;
  border-color: $cor4;
}


.menuTitle{
  display: flex;
}

.menuTitle img{
  margin: 20px 0px 0px 40px;
  height: 48px;
  width: 48px;
}

.menuTitle h1{
  font-size: 36px;
  color: $cor4;
  padding: 20px 0 0 10px;
}



</style>