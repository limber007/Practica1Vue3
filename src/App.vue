<!-- src/App.vue -->
<template>
  <div id="app">
    <h1>Gestión de Contactos</h1>
    <ContactList />
  </div>
</template>

<script>
import ContactList from './components/ContactList.vue';

export default {
  components: {
    ContactList
  }
};
</script>
