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
    <form class="bar" v-on:submit.prevent="createPost()" v-bind:key="book.id">
      <img v-if="errors.length > 0" v-bind:src="`https://http.cat/${errorStatus}`" />
      <ul>
        <li v-for="error in errors" v-bind:key="error">{{ error }}</li>
      </ul>
      <strong>New Comment:</strong>
      <input type="text" v-model="newPostParams.comment" />
      <input type="submit" value="Submit" />
      <p></p>
    </form>

    <div class="row icon-boxes">
      <div class="row-md-6 row-lg-3 d-flex align-items-stretch mb-5 mb-lg-0" data-aos="zoom-in" data-aos-delay="200">
        <div class="icon-box">
          <!-- <div class="icon"><i class="ri-palette-line"></i></div> -->
          <div v-for="post in book.posts.reverse()" v-bind:key="post.id">
            <h4 class="title">
              <a href="">{{ post.user.name + ":" }}</a>
            </h4>
            <p class="description">{{ post.comment }}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style>
.home {
  padding-top: 75px;
  max-width: 30%;
  /* text-align: center; */
  margin-left: auto;
  margin-right: auto;
}
/* .icon-box {
  margin-left: 30px;
} */
/* .comments {
  border-bottom: 2px solid #0287ec;
} */
img {
  max-width: 20%;
  height: auto;
}
.bar {
  border-bottom: 2px solid #080808;
  margin-bottom: 30px;
}
</style>
