<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <ContactTable />
  </div>
</template>

<script>
// @ is an alias to /src
import ContactTable from "@/components/ContactTable.vue";

export default {
  name: 'ContactView',
  components: {
    ContactTable
  }
}
</script>
