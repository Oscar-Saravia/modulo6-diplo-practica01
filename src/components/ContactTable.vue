<template>
  <div>
    <h1>{{ title }}</h1>
    <input type="text" v-model="searchQuery" placeholder="Buscar contacto por nombre y/o correo email...">
    <table>
      <thead>
        <tr>
          <th>ID</th>
          <th>Name</th>
          <th>Email</th>
          <th>Address</th>
          <th>Phone</th>
          <th>Country</th>
          <th>City</th>
          <th></th>
        </tr>
        <tr>
          <th>👤📲</th>
          <th><input type="text" v-model="emptyContact.name" placeholder="Name"></th>
          <th><input type="email" v-model="emptyContact.email" placeholder="Email"></th>
          <th><input type="text" v-model="emptyContact.address" placeholder="Address"></th>
          <th><input type="tel" v-model="emptyContact.phone" placeholder="Phone"></th>
          <th><input type="text" v-model="emptyContact.country" placeholder="Country"></th>
          <th><input type="text" v-model="emptyContact.city" placeholder="City"></th>
          <th>
            <button @click="addContact">Save</button>
          </th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="contact in filteredContacts" :key="contact.id">
          <td>{{ contact.id }}</td>
          <td>{{ contact.name }}</td>
          <td>{{ contact.email }}</td>
          <td>{{ contact.address }}</td>
          <td>{{ contact.phone }}</td>
          <td>{{ contact.country }}</td>
          <td>{{ contact.city }}</td>
          <td>
            <button @click="editContact(contact)">Edit</button>
            <button @click="deleteContact(contact.id)">Delete</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import contacts from '../seed/contacts-data.js'

export default {
  name: 'ContactTable',
  data() {
    return {
      title: 'Lista de Contactos',
      emptyContact: this.createEmptyContact(),
      contacts,
      searchQuery: ''
    }
  },
  computed: {
    filteredContacts() {
      return this.contacts.filter(contact => {
        return contact.name.toLowerCase().includes(this.searchQuery.toLowerCase()) ||
               contact.email.toLowerCase().includes(this.searchQuery.toLowerCase());
      });
    }
  },
  methods: {
    createEmptyContact() {
      return {
        id: null,
        name: '',
        email: '',
        address: '',
        phone: '',
        country: '',
        city: ''
      }
    },
    addContact() {
      let id = this.emptyContact.id ? this.emptyContact.id : this.contacts.length + 1;
      
      if (this.emptyContact.id) {
        const index = this.contacts.findIndex(contact => contact.id === this.emptyContact.id);
        if (index !== -1) {
          this.contacts.splice(index, 1, { ...this.emptyContact });
        }
      } else {
        this.contacts.push({ ...this.emptyContact, id });
      }

      this.emptyContact = this.createEmptyContact();
    },
    editContact(contact) {
      this.emptyContact = { ...contact };
    },
    deleteContact(id) {
      this.contacts = this.contacts.filter(contact => contact.id !== id);
    },
  }
}
</script>

<style scoped>
h1 {
  color: #42b983;
  text-align: center;
  margin-bottom: 20px;
}
input[type="text"], input[type="email"], input[type="tel"] {
  width: 100%;
  padding: 8px;
  margin: 5px 0;
  box-sizing: border-box;
}
table {
  width: 100%;
  border-collapse: collapse;
}
th, td {
  border: 1px solid #ddd;
  padding: 8px;
  text-align: left;
}
th {
  background-color: #f2f2f2;
}
button {
  background-color: #42b983;
  border: none;
  color: white;
  padding: 10px;
  cursor: pointer;
}
button:hover {
  background-color: #36a275;
}
</style>
