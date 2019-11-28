<template>
  <v-container>
    <v-layout align-center justify-center row fill-height>
      <v-flex>
        <h1 class="headline">Data Tables</h1>
        <v-data-table
          :headers="headers"
          :items="desserts"
          class="elevation-1"
        >
          <template v-slot:items="props">
            <td class="text-xs-center">{{ props.item.userId }}</td>
            <td class="text-xs-center">{{ props.item.title }}</td>
            <td class="text-xs-center">{{ props.item.completed }}</td>
          </template>
        </v-data-table>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
import axios from 'axios';

export default {
  name: 'HelloWorld',
  data: ()=> ({
    headers: [
      { text: '使用者編號',  align: 'center', value: 'userId' },
      { text: '標題',  align: 'center', value: 'title' },
      { text: '是否完成',  align: 'center', value: 'completed' }
    ],
    desserts: []
  }),
  created() {this.getTodoList()},
  methods: {
    getTodoList() {
      axios.get('https://jsonplaceholder.typicode.com/todos')
        .then((response) => {
          this.desserts = response.data
          return response.data
          console.log(response.data);
        })
        .catch((error) => {
          console.log(error);
        })
    }
  }
}
</script>
