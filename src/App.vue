<template>
  <div id="app">
    <div v-for="element in bookList" :key="element.id">
      <book :bookData="element"></book>
    </div>
  </div>
</template>

<script>
import bookList from "./bookList.json";
import book from "./components/book.vue";

export default {
  name: "App",
  data() {
    return {
      bookList
    };
  },
  components: {
    book
  }
};
</script>

<style></style>
