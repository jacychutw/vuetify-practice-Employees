<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >
      <v-icon class="mr-2">
        mdi-account-box-multiple
      </v-icon>
        Employee Data
    </v-app-bar>

    <v-main>
    <InputForm @refreshTable="refreshDataTable"/>
      <v-data-table
        :headers="headers"
        :items="employees"
        class="elevation-1"
      ></v-data-table>
    </v-main>
  </v-app>
</template>

<script>
import InputForm from './components/InputForm.vue'
//import DataTable from './components/DataTable.vue'

export default {
  name: 'App',
  components: {
    InputForm,
  },
  data () {
    return {
      headers: [
        {
          text: 'ID',
          align: 'start',
          sortable: true,
          value: 'id',
        },
        { text: 'Name', value: 'name' },
        { text: 'Phone', value: 'phone' },
        { text: 'Profession', value: 'profession' },
      ],
      employees: [
        { id: 1, name: "Chandler Bing", phone: '305-917-1301', profession: 'IT Manager' },
        { id: 2, name: "Ross Geller", phone: '210-684-8953', profession: 'Paleontologist' },
        { id: 3, name: "Rachel Green", phone: '765-338-0312', profession: 'Waitress'},
        { id: 4, name: "Monica Geller", phone: '714-541-3336', profession: 'Head Chef' },
        { id: 5, name: "Joey Tribbiani", phone: '972-297-6037', profession: 'Actor' },
        { id: 6, name: "Phoebe Buffay", phone: '760-318-8376', profession: 'Masseuse' }
      ],
    }
  },
  methods: {
    refreshDataTable(employeeData) {
      console.log(employeeData)
      let num = this.employees.length;
      this.employees.push({id: (num+1), name: employeeData[0], phone: employeeData[1], profession: employeeData[2] })
    }
  }
}
</script>
