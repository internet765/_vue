<template>
  <form action="" class="form" @submit.prevent>
    <h4 style='margin-bottom: 10px'>Создание поста</h4>
    <my-input
      v-model:value="post.title"
      placeholder="Название"
    ></my-input>
    <my-input
      v-model:value="post.body"
      placeholder="Описание"
    ></my-input>
    <my-button @click="createPost" style="align-self: flex-end">Создать</my-button
    >
  </form>
</template>

<script>
import MyInput from "./ui/MyInput.vue";
export default {
  components: { MyInput },
  data() {
    return {
      post: {
        body: "",
        title: "",
      },
    };
  },
  methods: {
    createPost() {
      if (this.post.title.length > 0 && this.post.body.length > 0) {
        this.post.id = Date.now();
        this.$emit("create", this.post);
        this.post = {
          body: "",
          title: "",
        };
      }
    },
  },
};
</script>

<style>
.form {
  display: flex;
  flex-direction: column;
  padding: 15px;
}

.input {
  width: 100%;
  border: 1px solid rgb(120, 201, 120);
  padding: 5px;
  margin-bottom: 10px;
}
</style>
