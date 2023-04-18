<template>
  <div class="app font-monospace">
    <div class="content">
      <AppInfo :barchaKinolar="movies.length" :watchedMovies="movies.filter(item => item.favorite).length" />
      <div class="searchPanel">
        <SearchPanel :updTermHandler="updTermHandler" />
        <AppFilter :updFilterHandler="updFilterHandler" :filterName="filter" />
      </div>
      <!-- Hech qanday ma'lumot topilmadi -->
      <Box v-if="!movies.length && !isLoading" class="text-danger">Hech qanday ma'lumot topilmadi!</Box>
      <!-- Loader -->
      <Box v-else-if="isLoading" class="text-center">
        <Loader></Loader>
      </Box>
      <!-- Movie List componenti va undagi propslar -->
      <MovieList v-else :movies="onFilter(onSearchHandler(movies, term), filter)" @onToggle="onToggleHandler"
        @onDelete="onDeleteHandler" />
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
import axios from "axios";
import Box from "./ui/Box.vue";
import Loader from "./ui/Loader.vue";

export default {
  // Barcha componentlar
  components: {
    AppInfo,
    SearchPanel,
    AppFilter,
    MovieList,
    MovieAddForm,
    Box,
    Loader,
  },

  // Barcha ma'lumotlarni saqlab turuvchi storage
  data() {
    return {
      movies: [],
      // Search inputdan keladigan qiymatni saqlovchi storage
      term: '',
      filter: 'all',
      isLoading: false,
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
    // Filter funksiyasi
    onFilter(arr, filter) {
      switch (filter) {
        case 'popular':
          return arr.filter(item => item.like)
        case 'mostView':
          return arr.filter(item => item.view > 200)
        default:
          return arr
      }
    },
    updFilterHandler(filter) {
      this.filter = filter
    },
    // API 'dan ma'lumot olish funksiyasi
    async fetchMovie() {
      try {
        this.isLoading = true;
        const { data } = await axios.get('https://jsonplaceholder.typicode.com/posts?_limit=5');
        const newArr = data.map(i => ({
          id: i.id,
          name: i.title,
          view: i.id * 15,
          like: false,
          favorite: false,
        }))
        this.movies = newArr;
      } catch (error) {
        alert(error.message);
      } finally {
        this.isLoading = false;
      }
    },
  },
  // User saytga kirgan payt API'dan ma'lumot oladigan funksiyani ishlatadigan metod
  mounted() {
    this.fetchMovie();
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