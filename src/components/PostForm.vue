<template>
  <form @submit.prevent>
    <h4>Создание поста</h4>

    <input
      v-model="post.title"
      class="input"
      type="text"
      placeholder="Название"
    >

    <input
      v-model="post.body"
      class="input"
      type="text"
      placeholder="Описание"
    >

    <button class="btn" @click="createPost">
      Создать
    </button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      post: {
        title: '',
        body: '',
      }
    }
  },
  methods: {
    createPost() {
      this.post.id =  Date.now(),
      this.$emit('create', this.post);
      this.post = {
        title: '',
        body: '',
      }
    }
  },
}
</script>

<style>
  form {
    display: flex;
    flex-direction: column;
  }

  .input {
    width: 100%;
    margin-top: 15px;
    padding: 10px 15px;
    border: 1px solid darkgreen;
  }

  .btn {
    align-self: flex-end;
    margin-top: 15px;
    padding: 10px 15px;
    border: 1px solid teal;
    background-color: none;
    color: teal;
    cursor: pointer;
  }
</style>