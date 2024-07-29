<template>
    <div>
      <h3>Editar Contacto</h3>
      <form @submit.prevent="submitForm">
        <input v-model="contact.name" placeholder="Nombre" required />
        <input v-model="contact.email" placeholder="Email" required />
        <input v-model="contact.address" placeholder="Dirección" required />
        <input v-model="contact.phone" placeholder="Teléfono" required />
        <input v-model="contact.country" placeholder="País" required />
        <input v-model="contact.city" placeholder="Ciudad" required />
        <button type="submit">Guardar Cambios</button>
      </form>
    </div>
  </template>
  
  <script>
  export default {
    props: ['contact'],
    data() {
      return {
        contact: { ...this.contact }
      };
    },
    methods: {
      submitForm() {
        this.$emit('update', this.contact);
      }
    }
  };
  </script>