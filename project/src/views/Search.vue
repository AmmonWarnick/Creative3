<template>
  <div class="search">
    <h1 class="title">Find your Amigos</h1>
    <form id="form" class="search-form" v-on:submit.prevent="getMovies()">
      <i class="fas fa-search"></i
      ><input type="text" id="searchTerm" v-model="searchTerm" />
    </form>
    <div v-if="empty">
      <div class="empty-div"></div>
    </div>
    <div v-else>
      <div class="movies">
        <div class="movie" v-for="movie in searched" :key="movie.id">
          <div class="poster">
            <div v-if="posterExists(movie)">
              <img :src="movie.poster" />
            </div>
            <div v-else>
              <i class="fas fa-exclamation-circle"></i>
              <p class="missing">Image not found</p>
            </div>
            <div class="arrow"></div>
            <div v-if="isInWatchlist(movie)">
              <button class="sub-btn" @click="removeFromWatchlist(movie)">
                <i class="fas fa-minus-square"></i>
              </button>
              <div class="sub-tooltip">Remove from Watchlist</div>
            </div>
            <div v-else>
              <button class="add-btn" @click="addToWatchList(movie)">
                <i class="fas fa-plus-square"></i>
              </button>
              <div class="add-tooltip">Add to Watchlist</div>
            </div>
            <div class="overview">
              <p>{{ movie.overview }}</p>
            </div>
          </div>
          <div class="movie-info">
            <h1>{{ movie.title }}</h1>
            <p>{{ movie.rating }}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: "Search",
  data() {
    return {
      searchTerm: "",
    };
  },
  computed: {
    empty() {
      if (this.$root.$data.searched.length == 0) {
        return true;
      } else {
        return false;
      }
    },
    searched() {
      return this.$root.$data.searched;
    }
  },
  }

</script>

<style scoped>
.search {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

form {
  display: flex;
  width: 30%;
  margin-top: 1em;
  margin-right: 2em;
}

input {
  font-size: 20px;
  border: none !important;
  box-shadow: none !important;
  width: 100%;
  height: 40px;
  padding-left: 0.5em;
  margin-left: 0.5em;
}
</style>
