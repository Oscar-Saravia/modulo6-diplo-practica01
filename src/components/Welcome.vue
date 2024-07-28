<template>
  <div class="welcome">
    <h1>{{ content.title }}</h1>
    <p>Autor:<span>{{ content.author }}</span></p>
    <p>{{ content.model }}</p>
    <p>La aplicación puede realizar las siguientes acciones:</p>
    <ul>
      <li v-for="(desc, index) in content.requirements" :key="index">
        {{ desc }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'Welcome',
  props: {
    content: {
      type: Object,
      required: true
    }
  }
}
</script>

<style scoped lang="scss">
.welcome {
  padding: 20px;
}
h1 {
  color: #42b983;
}
p {
  font-size: 1.1em;
  line-height: 1.5;
  margin: 10px 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  margin: 5px 0;
}
span {
  display: block;
  margin: 5px 0;
}
</style>
