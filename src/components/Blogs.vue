<template>
  <div class="blog">
    <div class="search">
      <input type="text" name="searchText" id="searchText" v-model="searchText" placeholder="Type something to search..." />
    </div>
    <div class="results">
      <div class="multi">
        <h4><strong>Total results: {{ countObjects }}</strong></h4>
        <div class="blog-post" v-for="post in showSearchResults" :key="post.id">
          <h2 class="blog-title">{{ post.title }}</h2>
          <p class="blog-desc">{{ post.body | snippet }} ...</p>
          <button @click="viewPost(post.id)">View</button>
        </div>
      </div>
      <div class="single">
        <div class="single-blog-post">
          <h2 class="single-blog-title">{{ post.title }}</h2>
          <p class="single-blog-desc">{{ post.body }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "Blogs",
  data() {
    return {
      posts: [],
      post: {
        title: ""
      },
      searchText: "",
      count: 0
    };
  },
  methods: {
    viewPost(id) {
      axios
        .get(`https://jsonplaceholder.typicode.com/posts/${id}/`)
        .then(response => {
          this.post = response.data;
          console.log(this.post);
        })
        .catch(err => {
          console.log(err);
        });
    }
  },
  computed: {
      showSearchResults() {
          return this.posts.filter(post => {
              return post.title.match(this.searchText)
          })
      },
      countObjects() {
          return this.posts.filter(post => {
              return post.title.match(this.searchText)
          }).length
      }
  },
  created() {
    axios
      .get("https://jsonplaceholder.typicode.com/posts/")
      .then(response => {
        this.posts = response.data;
        this.count = this.posts.length;
      })
      .catch(err => {
        console.log(err);
      });
  }
};
</script>

<style>
.blog {
  margin-top: 20px;
}

.search {
    margin-top: 20px;
    display: flex;
    justify-content: center;
    align-items: center;
}

.search input {
    width: 400px;
    height: 60px;
    border: 2px solid teal;
    padding: 10px 20px;
    font-size: 22px;
    color: teal;
}

.results {
  margin-top: 20px;
  display: flex;
}

.multi,
.single {
  flex: 1;
}

.single {
  position: fixed;
  top: 200px;
  right: 40px;
  margin-top: 20px;
}

.blog-post {
  padding: 20px;
  width: 400px;
  height: 200px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.15);
  background: #d4d9d1;
  margin: 25px;
  border: 1px solid rgba(0, 0, 0, 0.15);
}

.blog-title {
  font-size: 22px;
  color: teal;
  margin-bottom: 20px;
}

.blog-desc {
  font-size: 14px;
  color: midnightblue;
}

.single-blog-post {
  padding: 20px;
  width: 400px;
  height: 400px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.15);
  background: #fff;
  margin: 25px;
}

.single-blog-title {
  font-size: 22px;
  color: orangered;
  margin-bottom: 20px;
}

.single-blog-desc {
  font-size: 14px;
  color: midnightblue;
}
</style>