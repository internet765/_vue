<template>
  <div class="posts">
    <div>
      <div class="post">
        Название: <strong>{{ post.title }}</strong>
      </div>
      <div class="post">
        Описание: <strong>{{ post.body }}</strong>
      </div>
    </div>
    <div class="post__btn">
      <my-button @click="$emit('remove', post)">Удалить</my-button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    post: {
      type: Object,
      required: true,
    },
  },
  methods: {
    remove() {

    },
  },
};
</script>

<style scope>
.posts {
  display: flex;
  justify-content: space-between;
  align-items: center;
  border: 2px solid rgb(120, 201, 120);
  padding: 10px;
  margin-bottom: 10px;
}
</style>