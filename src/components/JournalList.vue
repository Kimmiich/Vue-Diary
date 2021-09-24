<template>
  <section>
    <Journal v-if="journal.title != null" :journal="journal" />
    <ul>
      <h2>Samling</h2>
      <li
        v-for="(journal, index) in sort(journals)"
        :key="index"
        @click="getJournal(journal)"
      >
        {{ journal.title }} || {{ journal.date }}
      </li>
    </ul>
  </section>
</template>

<script>
import Journal from './Jornal.vue';
import journals from '../App.vue';
export default {
  name: 'JournalList',
  props: {
    journals,
  },
  components: { Journal },
  data() {
    return {
      journal: {},
    };
  },
  methods: {
    sort(array) {
      if (array != null) {
        return array.slice().sort((a, b) => {
          return new Date(b.date) - new Date(a.date);
        });
      }
    },
    getJournal(data) {
      this.journal = data;
    },
  },
};
</script>

<style>
section {
  display: flex;
  flex-flow: row nowrap;

  width: 100vw;
  justify-content: space-evenly;
}
ul {
  order: 1;
  width: 35%;
  padding: 5px;
}
li {
  list-style: none;
  cursor: pointer;
  transition: 0.2s linear;
}

li:hover {
  transform: scale(1.1);
}
</style>
