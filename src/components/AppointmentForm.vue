<!-- src/components/AppointmentForm.vue -->
<template>
    <form @submit.prevent="handleSubmit">
      <div class="form-row">
        <div v-for="(value, key) in form" :key="key" class="form-group">
          <label :style="{ color: value.trim() ? 'black' : 'red' }">
            {{ key.charAt(0).toUpperCase() + key.slice(1) }}:
          </label>
          <input
            v-if="key !== 'gravedad'"
            :type="key === 'fecha' ? 'date' : key === 'hora' ? 'time' : 'text'"
            :name="key"
            v-model="form[key]"
          />
          <select v-if="key === 'gravedad'" v-model="form[key]">
            <option disabled value="">Seleccione</option>
            <option value="Baja">Baja</option>
            <option value="Media">Media</option>
            <option value="Alta">Alta</option>
          </select>
        </div>
      </div>
      <div class="form-button">
        <button type="submit" :disabled="!isFormValid">Agregar</button>
      </div>
    </form>
  </template>
  
  <script>
  export default {
    data() {
      return {
        form: {
          paciente: '',
          fecha: '',
          hora: '',
          gravedad: '',
          motivo: ''
        }
      };
    },
    computed: {
      isFormValid() {
        return Object.values(this.form).every(value => value.trim() !== '');
      }
    },
    methods: {
      handleSubmit() {
        this.$emit('add-appointment', this.form);
        this.form = {
          paciente: '',
          fecha: '',
          hora: '',
          gravedad: '',
          motivo: ''
        };
      }
    }
  };
  </script>
  
  <style scoped>
  form {
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 10px;
    background-color: #f9f9f9;
    font-family: 'Roboto', sans-serif;
  }
  
  .form-row {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    width: 100%;
  }
  
  .form-group {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    margin-bottom: 10px;
    width: calc(20% - 10px);
  }
  
  form label {
    margin-bottom: 5px;
  }
  
  form input,
  form select {
    width: 100%;
    padding: 5px;
    border: 1px solid #ccc;
    border-radius: 5px;
  }
  
  .form-button {
    width: 100%;
    display: flex;
    justify-content: center;
    margin-top: 20px;
  }
  
  button {
    padding: 10px 20px;
    background-color: #007bff;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
  }
  
  button:disabled {
    background-color: #cccccc;
  }
  </style>
  
  
  
  