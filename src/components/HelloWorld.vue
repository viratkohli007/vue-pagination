<template>
  <div>
    <h1 align="center">Hello</h1>
    <div style="height:50px"></div>
    <v-paginator ></v-paginator>
  </div>
</template>

<script>
import Paginator from './paginator.vue'
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  },
  components: {
    'v-paginator': Paginator
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
