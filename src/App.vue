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
    <InputForm @refreshTable="refreshDataTable" />
    <DataTable v-bind:parentVal="updataEmp" />
    </v-main>
  </v-app>
</template>

<script>
import InputForm from './components/InputForm.vue'
import DataTable from './components/DataTable.vue'

export default {
  name: 'App',
  components: {
    InputForm,
    DataTable
  },
  data () {
    return {
      updataEmp:[],
    }
  },
  methods: {
    refreshDataTable(employeeData) {
      this.updataEmp = employeeData;
      // console.log(employeeData)
      // let num = this.employees.length;
      // this.employees.push({id: (num+1), name: employeeData[0], phone: employeeData[1], profession: employeeData[2] })
    }
  }
}
</script>
