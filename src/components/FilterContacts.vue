<!-- src/components/FilterContacts.vue -->
<template>
    <input v-model="query" @input="filterContacts" placeholder="Buscar por nombre o email" />
  </template>
  
<script>
export default {
    data() {
      return {
        query: ''
      };
    },
    methods: {
      filterContacts() {
        this.$emit('filter', this.query);
      }
    }
 };
</script>
