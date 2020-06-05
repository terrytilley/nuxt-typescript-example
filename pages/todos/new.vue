<template>
  <v-layout column>
    <v-flex xs12>
      <v-form ref="form">
        <v-text-field v-model="title" label="Name" required></v-text-field>
      </v-form>
      <v-btn color="primary" @click="submit">
        Submit
      </v-btn>
    </v-flex>
  </v-layout>
</template>

<script>
import axios from 'axios'

export default {
  data() {
    return {
      title: ''
    }
  },
  methods: {
    async submit() {
      const { data } = await axios.post(
        'https://jsonplaceholder.typicode.com/todos',
        {
          title: this.title
        }
      )
      console.log('🚀', data)
    }
  }
}
</script>
