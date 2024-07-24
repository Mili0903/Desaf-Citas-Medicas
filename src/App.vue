<!-- src/App.vue -->
<template>
  <div id="app">
    <h1>Administrador de Citas Médicas</h1>
    <AppointmentForm @add-appointment="addAppointment" />
    <p v-if="appointments.length === 0">Aún no hay consultas registradas</p>
    <div class="appointments-container">
      <AppointmentCard
        v-for="(appointment, index) in appointments"
        :key="index"
        :appointment="appointment"
        @delete-appointment="deleteAppointment"
      />
    </div>
  </div>
</template>

<script>
import AppointmentForm from './components/AppointmentForm.vue';
import AppointmentCard from './components/AppointmentCard.vue';

export default {
  name: 'App',
  components: {
    AppointmentForm,
    AppointmentCard
  },
  data() {
    return {
      appointments: []
    };
  },
  methods: {
    addAppointment(appointment) {
      this.appointments.push(appointment);
    },
    deleteAppointment(appointmentToDelete) {
      this.appointments = this.appointments.filter(
        appointment => appointment !== appointmentToDelete
      );
    }
  }
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;500;700&display=swap');

#app {
  margin: 20px;
  text-align: center;
  font-family: 'Roboto', sans-serif;
}

h1 {
  font-weight: 700;
}

.appointments-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 10px;
}
</style>




