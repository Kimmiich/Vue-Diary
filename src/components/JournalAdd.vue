<template>
  <section>
    <form @submit="handleSubmit">
      <label for="title">Rubrik: </label>
      <input type="text" v-model="post.title" id="title" />
      <label for="date">Datum: </label>
      <input type="date" v-model="post.date" id="date" />
      <label for="text">Text: </label>
      <input type="text" v-model="post.text" id="text" />
      <button>Spara</button>
    </form>
  </section>
</template>

<script>
export default {
  name: 'JournalAdd',
  props: {
    post: {
      type: Object,
    },
  },
  methods: {
    handleSubmit(evt) {
      this.$emit('save', evt);
    },
  },
};
</script>

<style></style>
