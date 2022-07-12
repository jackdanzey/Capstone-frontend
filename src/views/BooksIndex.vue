<script>
import axios from "axios";
export default {
  data: function () {
    return {
      message: "All Books",
      books: [],
      nameFilter: "",
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
    filterBooks: function () {
      return this.books.filter((book) => {
        let lowerName = book.name.toLowerCase();
        let lowerNameFilter = this.nameFilter.toLowerCase();
        return lowerName.includes(lowerNameFilter);
      });
    },
    sortByTitle: function () {
      this.books.sort((a, b) => (a.name.toLowerCase() > b.name.toLowerCase() ? 1 : -1));
    },
  },
};
</script>

<template>
  <div class="books">
    <p>
      Search by title
      <input type="text" v-model="nameFilter" list="titles" />
      <datalist id="titles">
        <option v-for="book in books" v-bind:key="book.id" v-bind:to="`/books/${book.id}`">{{ book.name }}</option>
        <div class="dropdown-menu" aria-labelledby="dropdownMenu2">
          <router-link v-for="book in books" v-bind:key="book.id" class="dropdown-item" v-bind:to="`/books/${book.id}`">
            {{ book.name }}
          </router-link>
        </div>
      </datalist>
      <button v-on:click="sortByTitle()">Sort by title</button>
    </p>
    <!-- <div v-for="book in books" v-bind:key="book.id">
      <p>Title: {{ book.name }}</p>
      <p>Rating: {{ book.rating }}</p>
      <p><router-link v-bind:to="`/books/${book.id}`">See book page</router-link></p>
      <img v-bind:src="book.image" v-bind:alt="book.name" />
    </div> -->
    <div class="col-sm-6" v-for="book in filterBooks()" v-bind:key="book.id">
      <div class="card" style="width: 18rem">
        <img v-bind:src="book.image" class="card-img-top" v-bind:alt="book.name" />
        <div class="card-body">
          <h5 class="card-title">{{ book.name }}</h5>
          <p class="card-text">{{ book.rating }}</p>
          <p><router-link v-bind:to="`/books/${book.id}`">See book page</router-link></p>
          <!-- <a href="#" class="btn btn-primary">Go somewhere</a> -->
        </div>
      </div>
    </div>
    <!-- <div v-for="book in filterBooks()" v-bind:key="book.id">
      <h2>{{ book.name }}</h2>
      <img v-bind:src="book.image" v-bind:alt="book.image" />
      <router-link v-bind:to="`/books/${book.id}`">More details</router-link>
    </div> -->
  </div>
</template>

<style>
img {
  width: 20%;
  height: auto;
}
.card img {
  object-fit: cover;
  height: auto;
}
</style>
