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
  <section id="hero" class="d-flex align-items-center">
    <div class="books container position-relative" data-aos="fade-up" data-aos-delay="100">
      <div class="row justify-content-center">
        <div class="search">
          Search by title
          <input type="text" v-model="nameFilter" list="titles" />
          <datalist id="titles">
            <option v-for="book in books" v-bind:key="book.id" v-bind:to="`/books/${book.id}`">{{ book.name }}</option>
            <div class="dropdown-menu" aria-labelledby="dropdownMenu2">
              <router-link
                v-for="book in books"
                v-bind:key="book.id"
                class="dropdown-item"
                v-bind:to="`/books/${book.id}`"
              >
                {{ book.name }}
              </router-link>
            </div>
          </datalist>
          <button v-on:click="sortByTitle()">Sort by title</button>
        </div>
      </div>
      <!-- <div v-for="book in books" v-bind:key="book.id">
      <p>Title: {{ book.name }}</p>
      <p>Rating: {{ book.rating }}</p>
      <p><router-link v-bind:to="`/books/${book.id}`">See book page</router-link></p>
      <img v-bind:src="book.image" v-bind:alt="book.name" />
    </div> -->
      <!-- <div class="col-sm-6" v-for="book in filterBooks()" v-bind:key="book.id">
        <div class="card" style="width: 18rem">
          <img v-bind:src="book.image" class="card-img-top" v-bind:alt="book.name" />
          <div class="card-body">
            <h5 class="card-title">{{ book.name }}</h5>
            <p class="card-text">{{ book.rating }}</p>
            <p><router-link v-bind:to="`/books/${book.id}`">See book page</router-link></p> -->
      <!-- <a href="#" class="btn btn-primary">Go somewhere</a> -->
      <!-- </div>
        </div> -->
      <!-- </div> -->
      <div class="row w-100">
        <div
          v-for="book in filterBooks()"
          v-bind:key="book.id"
          class="col-md-6 col-lg-3 d-flex align-items-stretch mb-5 mb-lg-0 p-lg-1"
          data-aos="zoom-in"
          data-aos-delay="200"
        >
          <div class="icon-box">
            <p>Title: {{ book.name }}</p>
            <p>Rating: {{ book.rating }}</p>
            <p><router-link v-bind:to="`/books/${book.id}`">See Book Page</router-link></p>
            <img v-bind:src="book.image" v-bind:alt="book.image" />
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style>
#hero {
  padding-top: 100px;
}
/* .row {
  padding-top: 50px;
} */
img {
  min-width: 60%;
  height: auto;
}
</style>
