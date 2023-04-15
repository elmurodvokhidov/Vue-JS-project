<template>
  <div class="app font-monospace">
    <div class="content">
      <AppInfo :barchaKinolar="movies.length" :watchedMovies="movies.filter(item => item.favorite).length" />
      <div class="searchPanel">
        <SearchPanel />
        <AppFilter />
      </div>
      <MovieList :movies="movies" />
      <MovieAddForm @createItem="createItem" />
    </div>
  </div>
</template>

<script>
import AppInfo from "@/components/AppInfo.vue";
import SearchPanel from "@/components/SearchPanel.vue";
import AppFilter from "@/components/AppFilter.vue";
import MovieList from "@/components/MovieList.vue";
import MovieAddForm from "@/components/MovieAddForm.vue";

export default {
  components: {
    AppInfo,
    SearchPanel,
    AppFilter,
    MovieList,
    MovieAddForm,
  },

  data() {
    return {
      movies: [
        {
          name: 'Man in black',
          view: 787,
          favorite: true,
          like: true,
        },
        {
          name: 'Titanic',
          view: 145,
          favorite: true,
          like: false,
        },
        {
          name: 'Avatar',
          view: 511,
          favorite: true,
          like: true,
        },
      ]
    }
  },

  methods: {
    createItem(item) {
      this.movies.push(item);
    }
  },
}
</script>

<style>
.app {
  height: 100vh;
  color: black;
}

.content {
  width: 1000px;
  min-height: 700px;
  margin: 0 auto;
  padding: 5rem 0;
  background-color: white;
}

.searchPanel {
  margin-top: 2rem;
  padding: 1.5rem;
  background-color: #fcfaf5;
  border-radius: 4px;
  box-shadow: 15px 15px 15px rgba(0, 0, 0, 0.15);
}
</style>