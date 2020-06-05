<template>
  <v-layout column>
    <v-flex xs12>
      <v-card class="mx-auto" tile>
        <v-data-table :headers="headers" :items="todos" class="elevation-1">
          <template v-slot:item.completed="{ item }">
            <v-icon v-if="item.completed" large color="green darken-2">
              mdi-check
            </v-icon>
            <v-icon v-else large color="red darken-2">
              mdi-close
            </v-icon>
          </template>
        </v-data-table>
      </v-card>
    </v-flex>
  </v-layout>
</template>

<script>
import axios from 'axios'

export default {
  async asyncData() {
    const { data } = await axios.get(
      'https://jsonplaceholder.typicode.com/todos'
    )
    return { todos: data }
  },
  data() {
    return {
      headers: [
        { text: 'Title', value: 'title' },
        { text: 'Completed', value: 'completed' }
      ]
    }
  }
}
</script>
