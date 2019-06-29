<template>
  <v-app>
    <v-content>
      <Todo/>
    </v-content>
  </v-app>
</template>

<script>
import Todo from './components/Todo'

export default {
  name: 'App',
  components: {
    Todo
  },
  data () {
    return {}
  }
}
</script>
