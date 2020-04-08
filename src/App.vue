<template>
  <div id="main-app" class="container">
    <h4>{{ title }}</h4>

    <div class="row justify-content-center">
      <font-awesome-icon icon="plus" class="mr-2" />Add Appointment
      <Appointment-List :appointments="appointments" />
    </div>
  </div>
</template>

<script>
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";
import axios from "axios";

import AppointmentList from "./components/AppointmentList";

export default {
  name: "MainApp",
  data: function() {
    return {
      title: "Appointment List!!",
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
  }
};
</script>
