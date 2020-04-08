<template>
  <div id="main-app" class="container">
    <div class="row justify-content-center">
      <font-awesome-icon icon="plus" class="mr-2" />Add Appointment
      <Appointment-List :appointments="appointments" @remove="removeItem" />
    </div>
  </div>
</template>

<script>
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";
import _ from "lodash";
import axios from "axios";

import AppointmentList from "./components/AppointmentList";

export default {
  name: "MainApp",
  data: function() {
    return {
      appointments: []
    };
  },
  components: {
    FontAwesomeIcon,
    AppointmentList
  },
  mounted() {
    //lifecycle method
    axios
      .get("./data/appointments.json")
      .then(response => (this.appointments = response.data));
  },
  methods: {
    removeItem: function(apt) {
      this.appointments = _.without(this.appointments, apt);
    }
  }
};
</script>
