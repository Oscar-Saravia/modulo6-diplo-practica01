<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <Welcome :content="content"/>
  </div>
</template>

<script>
import Welcome from '@/components/Welcome.vue'

export default {
  name: 'HomeView',
  data() {
    return {
      // 'Ing. Sergio Daza Mendoza'
      content: {
        title: 'Modulo 6 - Practica Vue 3',
        author: 'Oscar Saravia Veizaga',
        model: 'Tabla Contacto: ID, Name, Email, Address, Phone, Country, City',
        requirements: [
          'Listar los contactos',
          'Agregar un nuevo contacto',
          'Eliminar un contacto',
          'Editar un contacto',
          'Filtrar los contactos por nombre y/o correo electrónico',
        ]
      }
    }
  },
  components: {
    Welcome
  }
}
</script>

<style scoped lang="scss">
.home {
  text-align: center;
}
img {
  margin: 20px auto;
}
</style>
