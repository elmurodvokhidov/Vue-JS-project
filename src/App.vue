<template>
  <div class="app font-monospace">
    <div class="content">
      <AppInfo />
      <div class="searchPanel">
        <SearchPanel />
        <AppFilter />
      </div>
      <MovieList />
      <MovieAddForm />
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
  }
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