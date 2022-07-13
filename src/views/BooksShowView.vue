<script>
import axios from "axios";
export default {
  data: function () {
    return {
      message: "Welcome to Vue.js!",
      book: {},
      newPostParams: {},
      errors: [],
      newRateParams: {},
      bookId: "",
    };
  },
  created: function () {
    axios.get("/books/" + this.$route.params.id + ".json").then((response) => {
      console.log(response.data);
      this.book = response.data;
      this.bookId = this.book.id;
      console.log(this.bookId);
      this.newPostParams.book_id = this.book.id;
      this.newRateParams.book_id = this.book.id;
    });
  },
  methods: {
    createPost: function () {
      axios
        .post("/posts.json", this.newPostParams)
        .then((response) => {
          console.log("post create", response);
          // this.$router.push("/books/" + this.$route.params.id);
          location.reload();
        })
        .catch((error) => {
          console.log("posts create error", error.response);
          this.errors = error.response.data.errors;
          this.errorStatus = error.response.status;
        });
    },
    createRating: function () {
      axios
        .post("/ratings.json", this.newRateParams)
        .then((response) => {
          console.log("rating create", response);
          // this.$router.push("/books/" + this.$route.params.id);
          location.reload();
        })
        .catch((error) => {
          console.log("rating create error", error.response);
          this.errors = error.response.data.errors;
          this.errorStatus = error.response.status;
        });
    },
  },
};
</script>

<template>
  <div class="home">
    <h2>{{ book.name }}</h2>
    <p>Rating: {{ book.rating }}</p>
    <img v-bind:src="book.image" v-bind:alt="book.name" />
    <form v-on:submit.prevent="createRating()" v-bind:key="book.id">
      <img v-if="errors.length > 0" v-bind:src="`https://http.cat/${errorStatus}`" />
      <ul>
        <li v-for="error in errors" v-bind:key="error">{{ error }}</li>
      </ul>
      <strong>Rate 1-5:</strong>
      <input type="text" v-model="newRateParams.score" />
      <input type="submit" value="Submit" />
    </form>
    <form v-on:submit.prevent="createPost()" v-bind:key="book.id">
      <img v-if="errors.length > 0" v-bind:src="`https://http.cat/${errorStatus}`" />
      <ul>
        <li v-for="error in errors" v-bind:key="error">{{ error }}</li>
      </ul>
      <strong>New Comment:</strong>
      <input type="text" v-model="newPostParams.comment" />
      <input type="submit" value="Submit" />
    </form>
    <div v-for="post in book.posts.reverse()" v-bind:key="post.id">
      <p>{{ post.user.name + " said: " + post.comment }}</p>
    </div>
  </div>
</template>

<style>
.home {
  padding-top: 75px;
  max-width: 40%;
}
img {
  max-width: 20%;
  height: auto;
}
</style>
