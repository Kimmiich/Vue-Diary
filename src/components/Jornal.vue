<template>
  <article>
    <h3>{{ journal.title }}</h3>
    <h6>{{ journal.date }}</h6>
    <p>{{ journal.text }}</p>
  </article>
</template>

<script>
import journal from './JournalList.vue';
export default {
  name: 'Journal',
  props: { journal },
};
</script>

<style>
article {
  order: 2;
  padding: 15px;
  margin-top: 20px;
  width: 50%;
  border: 1px solid black;
}
h3 {
  font-size: 1.4em;
  margin: 0px;
  text-decoration: underline;
}
h6 {
  margin: 0px;
  padding-left: 2px;
}
p {
  font-style: italic;
}
</style>
