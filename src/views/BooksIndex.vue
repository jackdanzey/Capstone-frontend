<script>
import axios from "axios";
export default {
  data: function () {
    return {
      message: "All Books",
      books: [],
    };
  },
  created: function () {
    this.indexBooks();
  },
  methods: {
    indexBooks: function () {
      axios.get("/books" + ".json").then((response) => {
        console.log("books index", response);
        this.books = response.data;
      });
    },
  },
};
</script>

<template>
  <div class="books">
    <div v-for="book in books" v-bind:key="book.id">
      <p>Title: {{ book.name }}</p>
      <p>Rating: {{ book.rating }}</p>
      <p><router-link v-bind:to="`/books/${book.id}`">See book page</router-link></p>
      <img v-bind:src="book.image" v-bind:alt="book.name" />
    </div>
  </div>
</template>

<style>
img {
  width: 20%;
  height: auto;
}
</style>
