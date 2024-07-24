<!-- src/components/AppointmentCard.vue -->
<template>
    <div :style="{ backgroundColor: getBackgroundColor(appointment.gravedad) }" class="card">
      <div class="card-content">
        <div class="card-item">
          <strong>Paciente:</strong>
          <p>{{ appointment.paciente }}</p>
        </div>
        <div class="card-item">
          <strong>Fecha:</strong>
          <p>{{ appointment.fecha }}</p>
        </div>
        <div class="card-item">
          <strong>Hora:</strong>
          <p>{{ appointment.hora }}</p>
        </div>
        <div class="card-item">
          <strong>Motivo:</strong>
          <p>{{ appointment.motivo }}</p>
        </div>
        <button @click="$emit('delete-appointment', appointment)">Eliminar</button>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      appointment: Object
    },
    methods: {
      getBackgroundColor(gravedad) {
        switch (gravedad) {
          case 'Alta':
            return 'red';
          case 'Media':
            return 'yellow';
          case 'Baja':
            return 'green';
          default:
            return 'white';
        }
      }
    }
  };
  </script>
  
  <style scoped>
  .card {
    width: 7cm;
    border: 1px solid #ccc;
    padding: 10px;
    margin-bottom: 10px;
    box-sizing: border-box;
    border-radius: 5px;
    font-family: 'Roboto', sans-serif;
  }
  
  .card-content {
    display: flex;
    flex-direction: column;
  }
  
  .card-item {
    margin-bottom: 10px;
  }
  
  .card-item strong {
    display: block;
    margin-bottom: 5px;
  }
  
  button {
    padding: 10px;
    background-color: #007bff;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    font-family: 'Roboto', sans-serif;
  }
  
  button:hover {
    background-color: #0056b3;
  }
  </style>
  
  
  
  