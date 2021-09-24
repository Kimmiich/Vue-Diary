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
  margin-top: 20px;
  width: 50%;
  border: 1px solid black;
}
</style>
