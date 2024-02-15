<template>
    <div>
      <h2>Registro</h2>
      <form @submit.prevent="register">
        <div>
          <label for="name">Nombre:</label>
          <input type="text" id="name" v-model="name">
        </div>
        <div>
          <label for="email">Email:</label>
          <input type="email" id="email" v-model="email">
        </div>
        <div>
          <label for="password">Contraseña:</label>
          <input type="password" id="password" v-model="password">
        </div>
        <div>
          <label for="password_confirmation">Confirmar Contraseña:</label>
          <input type="password" id="password_confirmation" v-model="passwordConfirmation">
        </div>
        <button type="submit">Registrarse</button>
      </form>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    name: 'Register',
    data() {
      return {
        name: '',
        email: '',
        password: '',
        passwordConfirmation: ''
      };
    },
    methods: {
      async register() {
        try {
          const response = await axios.post('http://127.0.0.1:8000/api/register', {
            name: this.name,
            email: this.email,
            password: this.password,
            password_confirmation: this.passwordConfirmation
          });
          console.log('Respuesta:', response.data);
          // Manejar la respuesta del servidor (por ejemplo, mostrar un mensaje de éxito al usuario)
        } catch (error) {
          console.error('Error:', error.response.data);
          // Manejar el error de registro (por ejemplo, mostrar mensajes de error al usuario)
        }
      }
    }
  };
  </script>
  
  <style scoped>
  /* Estilos específicos para este componente */
  </style>
  