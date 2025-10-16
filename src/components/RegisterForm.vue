<template>
  <div class="register-form">
    <h2>Registrar Usuario</h2>
    <form @submit.prevent="registrarUsuario">
      <div>
        <label>Gmail:</label>
        <input v-model="gmail" type="email" required />
      </div>
      <div>
        <label>Contraseña:</label>
        <input v-model="contrasena" type="password" required />
      </div>
      <button type="submit">Registrar</button>
    </form>
    <p v-if="mensaje">{{ mensaje }}</p>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "RegisterForm",
  data() {
    return {
      gmail: "",
      contrasena: "",
      mensaje: ""
    };
  },
  methods: {
    async registrarUsuario() {
      try {
        const res = await axios.post("http://localhost:3000/api/usuarios", {
          gmail: this.gmail,
          contrasena: this.contrasena
        });
        this.mensaje = "Usuario registrado correctamente!";
        this.gmail = "";
        this.contrasena = "";
      } catch (err) {
        console.error(err);
        this.mensaje = "Error al registrar usuario";
      }
    }
  }
};
</script>

<style scoped>
/* Contenedor centrado en toda la pantalla */
.container {
  display: flex;
  justify-content: center; 
  align-items: center;    
  height: 100vh;           
  background-color: #f0f4f8; 
  color: black
}

.register-form {
  width: 100%;
  max-width: 400px;
  padding: 30px;
  background-color: #ffffff;
  border-radius: 15px;
  box-shadow: 0 6px 20px rgba(0, 0, 0, 0.1);
  text-align: center;
  font-family: Arial, sans-serif;
}

.register-form h2 {
  color: #1e3a8a; /* azul oscuro */
  margin-bottom: 20px;
}

.form-group {
  margin-bottom: 15px;
  text-align: left;
}

.form-group label {
  display: block;
  margin-bottom: 5px;
  color: #1e40af; /* azul */
  font-weight: bold;
}

.form-group input {
  width: 100%;
  padding: 10px 12px;
  border: 1px solid #cbd5e1; /* gris claro */
  border-radius: 8px;
  outline: none;
  transition: border-color 0.2s;
}

.form-group input:focus {
  border-color: #3b82f6; /* azul brillante */
}

button {
  background-color: #3b82f6; /* azul brillante */
  color: white;
  border: none;
  padding: 10px 25px;
  border-radius: 8px;
  font-size: 16px;
  cursor: pointer;
  transition: background-color 0.2s;
}

button:hover {
  background-color: #2563eb; /* azul más oscuro */
}

.mensaje {
  margin-top: 15px;
  font-weight: bold;
  color: #1e3a8a;
}
.label {
  color: black;
}
</style>