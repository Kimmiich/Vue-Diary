<template>
  <section>
    <form @submit="handleSubmit">
      <h4>Ny tanke:</h4>
      <input
        type="text"
        v-model="post.title"
        id="title"
        placeholder="Rubrik..."
      />
      <input type="date" v-model="post.date" id="date" />
      <textarea
        v-model="post.text"
        id="text"
        placeholder="Skriv din text här..."
      />
      <button class="btn-save">Spara</button>
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

<style>
form {
  display: flex;
  flex-flow: row wrap;
  border: 1px solid black;
  padding: 10px;
  justify-content: center;
  max-width: 100%;
}
h4 {
  margin: 5px;
  width: 95%;
}

#title,
#date {
  width: 45%;
  margin: 5px;
}

#text {
  width: 93%;
  height: 90px;
  margin: 5px;
}

.btn-save {
  margin: 5px;
  width: 94%;
}
</style>
