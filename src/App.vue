<template>
  <div id="app">
    <header>
      <h1>Mina samlade tankar!</h1>
      <button @click="onClick">
        {{ clicked === true ? 'Stäng' : 'Lägg till' }}
      </button>
    </header>

    <JournalAdd :post="journal" @save="handleSubmit" v-if="clicked === true" />
    <JournalList :journals="journals" />
  </div>
</template>

<script>
import JournalList from './components/JournalList.vue';
import JournalAdd from './components/JournalAdd.vue';

export default {
  name: 'App',
  data() {
    return {
      journal: {},
      journals: [],
      clicked: false,
    };
  },
  components: {
    JournalList,
    JournalAdd,
  },
  created() {
    this.journals = JSON.parse(localStorage.getItem('Journal'));
    // console.log(this.journals);
  },
  methods: {
    onClick() {
      this.clicked = !this.clicked;
    },
    handleSubmit(evt) {
      evt.preventDefault();

      let newPost = {
        title: evt.target.title.value,
        date: evt.target.date.value,
        text: evt.target.text.value,
      };

      // console.log('Formulär sparat: ', newPost);

      if (localStorage.getItem('Journal') === null) {
        localStorage.setItem('Journal', JSON.stringify(this.journals));

        // console.log('saved to empty: ', journal);
      } else {
        let getSaved = JSON.parse(localStorage.getItem('Journal'));
        getSaved.push(newPost);
        localStorage.setItem('Journal', JSON.stringify(getSaved));
        // console.log('Added post: ', getSaved);
      }
      this.journals.push(newPost);
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
