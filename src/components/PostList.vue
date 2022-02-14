<template>
  <div class="container" v-if="posts.length > 0">
    <h3 style="margin: 10px 0 10px 0">Список пользователей</h3>
    <post-item
      :post="post"
      @remove="$emit('remove', post)"
      :key="post.id"
      v-for="post in posts"
    ></post-item>
  </div>
  <h2 v-else style="color: red">Список постов пуст</h2>
</template>

<script>
import PostItem from "./PostItem.vue";
export default {
  components: {
    PostItem,
  },
  props: {
    posts: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style >
</style>