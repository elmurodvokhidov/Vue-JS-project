<template>
  <div class="app font-monospace">
    <div class="content">
      <AppInfo :barchaKinolar="movies.length" :watchedMovies="movies.filter(item => item.favorite).length" />
      <div class="searchPanel">
        <SearchPanel :updTermHandler="updTermHandler" />
        <AppFilter />
      </div>
      <!-- Movie List componenti va undagi propslar -->
      <MovieList :movies="onSearchHandler(movies, term)" @onToggle="onToggleHandler" @onDelete="onDeleteHandler" />
      <!-- Movie Add Form componenti va undagi propslar -->
      <MovieAddForm @createItem="createItem" />
    </div>
  </div>
</template>

<script>
// Componentlarni import qilish
import AppInfo from "@/components/AppInfo.vue";
import SearchPanel from "@/components/SearchPanel.vue";
import AppFilter from "@/components/AppFilter.vue";
import MovieList from "@/components/MovieList.vue";
import MovieAddForm from "@/components/MovieAddForm.vue";

export default {
  // Barcha componentlar
  components: {
    AppInfo,
    SearchPanel,
    AppFilter,
    MovieList,
    MovieAddForm,
  },

  // Barcha ma'lumotlarni saqlab turuvchi storage
  data() {
    return {
      movies: [
        {
          name: 'Man in black',
          view: 787,
          favorite: true,
          like: true,
          id: 1,
        },
        {
          name: 'Titanic',
          view: 145,
          favorite: true,
          like: false,
          id: 2,
        },
        {
          name: 'Avatar',
          view: 511,
          favorite: true,
          like: true,
          id: 3,
        },
      ],
      // Search inputdan keladigan qiymatni saqlovchi storage
      term: '',
    }
  },

  methods: {
    // Yangi ma'lumot qo'shish funksiyasi
    createItem(item) {
      this.movies.push(item);
    },
    // onLike va onFavorite funksiyasi
    onToggleHandler({ id, prop }) {
      this.movies = this.movies.map(item => {
        if (item.id == id) {
          return { ...item, [prop]: !item[prop] }
        }
        return item;
      })
    },
    // Ma'lumotlarni o'chirish funksiyasi
    onDeleteHandler(id) {
      this.movies = this.movies.filter(item => item.id !== id)
    },
    // Search funksiyasi
    onSearchHandler(arr, term) {
      if (term.length == 0) {
        return arr
      }
      return arr.filter(item => item.name.toLowerCase().indexOf(term.toLowerCase()) > -1)
    },
    updTermHandler(term) {
      this.term = term
    },
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