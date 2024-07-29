<!-- src/components/AddContact.vue -->
<template>
    <form @submit.prevent="submitForm">
      <input v-model="newContact.name" placeholder="Nombre" required />
      <input v-model="newContact.email" placeholder="Email" required />
      <input v-model="newContact.address" placeholder="Dirección" required />
      <input v-model="newContact.phone" placeholder="Teléfono" required />
      <input v-model="newContact.country" placeholder="País" required />
      <input v-model="newContact.city" placeholder="Ciudad" required />
      <button type="submit">Agregar Contacto</button>
    </form>
  </template>
  
  <script>
  export default {
    data() {
      return {
        newContact: {
          name: '',
          email: '',
          address: '',
          phone: '',
          country: '',
          city: ''
        }
      };
    },
    methods: {
      submitForm() {
        this.$emit('add', { ...this.newContact });
        this.newContact = { name: '', email: '', address: '', phone: '', country: '', city: '' }; // Reiniciar formulario
      }
    }
  };
  </script>
  