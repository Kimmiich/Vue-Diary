<template>
  <section>
    <h2>Inlägg</h2>
    <Journal v-if="journal.title != null" :journal="journal" />
    <ul>
      <li
        v-for="(journal, index) in journals"
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
        return array.sort((a, b) => {
          return new Date(b.date) - new Date(a.date);
          //Vrf blir det en infinite loop med denna funktion? Kallar på den i li element journal in sort(journals)
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
li {
  list-style: none;
  cursor: pointer;
  transition: 0.2s linear;
}

li:hover {
  transform: scale(1.1);
}
</style>
