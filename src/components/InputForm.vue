<template>
  <div>
    <v-form>
      <v-container>
        <v-row>
          <v-col
            cols="12"
            sm="3"
          >
            <v-text-field
              label="Name"
              v-model="name"
              required
            ></v-text-field>
          </v-col>
          <v-col
            cols="12"
            sm="3"
          >
            <v-text-field
              label="Phone"
              v-model="phone"
              required
            ></v-text-field>
          </v-col>
          <v-col
            cols="12"
            sm="3"
          >
            <v-text-field
              label="Profession"
              v-model="profession"
              required
            ></v-text-field>
          </v-col>
          <v-col
            cols="12"
            sm="3"
          >
          <!-- <button>Send</button> -->
          <v-btn class="mt-3" @click="addEmployee">
            Send
          </v-btn>
          </v-col>
        </v-row>
      </v-container>
    </v-form>
  </div>
</template>

<script>
import { validationMixin } from "vuelidate";
import { required } from "vuelidate/lib/validators";

export default {
  mixins: [validationMixin],
  validations: {
    name: { required },
    phone: { required },
    profession: { required },
  },
  data() {
    return {
      name: "",
      phone: "",
      profession: ""
    }
  },
  methods: {
    addEmployee() {
      let employeeData= [this.name, this.phone, this.profession];
      //let empobj = {name: this.name, phone: this.phone}
      //console.log(empobj)
      this.$emit("refreshTable",employeeData);
      //this.$emit("refreshTable",empobj);
      this.name = "";
      this.phone = "";
      this.profession= "";
    }
  }
}
</script>
