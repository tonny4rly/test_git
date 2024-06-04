<template>
    <div>
      <form @submit.prevent="submitForm">
        <label for="name">Name:</label>
        <input type="text" id="name" v-model="formData.name" required>
  
        <label for="email">Email:</label>
        <input type="email" id="email" v-model="formData.email" required>
  
        <button type="submit">Submit</button>
      </form>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    data() {
      return {
        formData: {
          name: '',
          email: ''
        }
      };
    },
    methods: {
      submitForm() {
        // Validation supplémentaire avant de soumettre le formulaire
        if (this.formData.name && this.formData.email) {
          axios.post('http://localhost:8000/api/form', this.formData)
            .then(response => {
              console.log(response.data);
            })
            .catch(error => {
              console.error(error);
            });
        } else {
          alert('Please fill in all required fields.');
        }
      }
    }
  };
  </script>
  
  <style scoped>
    div {
      display: flex;
      align-items: center;
      justify-content: center;
      flex-direction: column;
      background-color: azure;
      margin: 10px;
      border-radius: 10px;
    }
    
    label {
      display: block;
      margin-bottom: 5px;
    }
    
    input {
      margin-bottom: 10px;
      padding: 5px;
      border: 1px solid;
      border-radius: 5px;
      outline: none;
    }
  
    form {
      padding-bottom: 5px;
      display: flex;
      align-items: center;
      justify-content: center;
      flex-direction: column;
      padding: 10px;
    }
    
    button {
      padding: 5px 10px;
    }
  </style>
  