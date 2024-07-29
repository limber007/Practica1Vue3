<!-- src/components/ContactList.vue -->
<template>
    <div>
      <h2>Lista de Contactos</h2>
      <ul>
        <li v-for="contact in filteredContacts" :key="contact.id">
          {{ contact.name }} - {{ contact.email }}
          <button @click="startEdit(contact)">Editar</button>
          <button @click="deleteContact(contact.id)">Eliminar</button>
        </li>
      </ul>
      <FilterContacts @filter="filterContacts" />
      <AddContact @add="addContact" />
      <EditContact v-if="editingContact" :contact="editingContact" @update="updateContact" />
    </div>
  </template>
  
  <script>
  import { contacts } from './data';
  import FilterContacts from './FilterContacts.vue';
  import AddContact from './AddContact.vue';
  import EditContact from './EditContact.vue';
  
  export default {
    components: { FilterContacts, AddContact, EditContact },
    data() {
      return {
        contacts: contacts,
        searchQuery: '',
        editingContact: null
      };
    },
    computed: {
      filteredContacts() {
        return this.contacts.filter(contact =>
          contact.name.includes(this.searchQuery) || contact.email.includes(this.searchQuery)
        );
      }
    },
    methods: {
      addContact(newContact) {
        this.contacts.push({ ...newContact, id: this.contacts.length + 1 });
      },
      deleteContact(id) {
        this.contacts = this.contacts.filter(contact => contact.id !== id);
      },
      startEdit(contact) {
        this.editingContact = { ...contact }; // Clonar para evitar mutaciones
      },
      updateContact(updatedContact) {
        const index = this.contacts.findIndex(contact => contact.id === updatedContact.id);
        if (index !== -1) {
          this.contacts.splice(index, 1, updatedContact);
        }
        this.editingContact = null; // Cerrar el formulario de edición
      },
      filterContacts(query) {
        this.searchQuery = query;
      }
    }
  };
  </script>
  