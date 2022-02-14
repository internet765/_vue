<template>
  <div class="root">
    <div>
      <my-button @click="addLike">LIKE</my-button>
      <my-button @click="addDislike">DISLIKE</my-button>
    </div>
    <div class="class">
      лайков: <strong>{{ likes }}</strong>
    </div>
    <h1>Страница с постами</h1>
    <my-button style="margin: 10px 0 10px 0" @click="showDialog"
      >Создать пользователя</my-button
    >
    <my-dialog v-model:show="dialogVisible">
      <post-form @create="createPost" />
    </my-dialog>
    <post-list :posts="posts" @remove="remove" v-if="!isLoading" />
    <div v-else>Идет Загрузка...</div>
  </div>
</template>

<script>
import PostForm from "./components/PostForm";
import PostList from "./components/PostList";
import axios from "axios";

export default {
  components: {
    PostList,
    PostForm,
  },
  data() {
    return {
      likes: 0,
      dislikes: 0,
      dialogVisible: false,
      isLoading: false,
      posts: [],
    };
  },
  methods: {
    addLike() {
      this.likes += 1;
    },
    addDislike() {
      if (this.likes > 0) this.likes -= 1;
    },
    createPost(post) {
      this.posts.unshift(post);
      this.dialogVisible = false;
    },
    remove(post) {
      this.posts = this.posts.filter((item) => item.id !== post.id);
    },
    showDialog() {
      this.dialogVisible = true;
    },
    async fetchPost() {
      try {
        this.isLoading = true;
        const res = await axios.get(
          "https://jsonplaceholder.typicode.com/posts?_limit=10"
        );
        this.posts = res.data;
      } catch (err) {
        alert("Ошибка");
      } finally {
        this.isLoading = false;
      }
    },
  },
  mounted() {
    this.fetchPost();
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.root {
  padding: 10px;
}

.class {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  background-color: #2c3e50;
}
</style>

