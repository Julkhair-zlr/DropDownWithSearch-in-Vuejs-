<script>
import NavBar from "./components/NavBar.vue";
import Home from "./components/Home.vue";
import SearchBar from "./components/SearchBar.vue";
import SearchBarCommants from "./components/SearchBarCommants.vue";
export default {
  components: { NavBar, Home, SearchBar, SearchBarCommants },
};
</script>
<template>
  <div>
    <div class="bg-white border-b-4 w-screen h-auto sm:h-[6vh]">
      <!-- <NavBar /> -->
    </div>
    <Home />
    <!-- <SearchBar /> -->
    <SearchBarCommants />
  </div>
</template>