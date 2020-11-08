<template>
  <div class="watchlist">
    <h1 class="title">My Friends</h1>
    <div class="wrapper">
      <div v-if="empty">
        <p class="empty-watchlist-msg">You have no friends :(</p>
      </div>
      <div v-else>
        <div class="movies">
          <div class="movie" v-for="movie in watchlist" :key="movie.id">
            <div class="poster">
              <div class="arrow"></div>
              <div v-if="isInWatchlist(movie)">
                <button class="sub-btn" @click="removeFromWatchlist(movie)">
                  <i class="fas fa-minus-square"></i>
                </button>
                <div class="sub-tooltip">Remove from Watchlist</div>
              </div>
              <div class="overview">
                <p>{{ movie.overview }}</p>
              </div>
            </div>
            <div class="movie-info">
              <h1>{{ movie.first_name }} {{ movie.last_name }}</h1>
              <p>{{ movie.email }}</p>
              <p>{{ movie.gender }}</p>
              <p>{{ movie.job }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Watchlist",
  computed: {
    watchlist() {
      return this.$root.$data.watchlist;
    },
    empty() {
      if (this.$root.$data.watchlist.length == 0) {
        return true;
      } else {
        return false;
      }
    },
  },
  methods: {
    isInWatchlist(movie) {
      for (let i = 0; i < this.$root.$data.watchlist.length; i++) {
        if (this.$root.$data.watchlist[i] === movie) {
            return true;
        }
      }
      return false;
    }
  }
};
</script>

<style>
.empty-watchlist-msg {
  font-size: 2.5em;
  padding-top: 1em;
  color: #ababab;
  font-style: italic;
}
</style>
