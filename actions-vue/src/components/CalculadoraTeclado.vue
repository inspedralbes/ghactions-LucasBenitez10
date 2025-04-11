<template>
    <div class="calculadora-container">
      <h1>Calculadora Vue</h1>
      
      <div class="resultado">
        <p v-if="numeroClicado !== null">Has clicadoo el número: <strong>{{ numeroClicado }}</strong></p>
        <p v-else>Clica un número</p>
      </div>
      
      <div class="teclado">
        <div class="fila" v-for="fila in filasTeclado" :key="fila.id">
          <button 
            v-for="numero in fila.numeros" 
            :key="numero" 
            class="tecla"
            @click="handleNumeroClick(numero)"
          >
            {{ numero }}
          </button>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'CalculadoraTeclado',
    data() {
      return {
        numeroClicado: null,
        filasTeclado: [
          { id: 1, numeros: [1, 2, 3] },
          { id: 2, numeros: [4, 5, 6] },
          { id: 3, numeros: [7, 8, 9] },
          { id: 4, numeros: [0] }
        ]
      }
    },
    methods: {
      handleNumeroClick(numero) {
        this.numeroClicado = numero;
        console.log(`Has clicado el número: ${numero}`);
      }
    }
  }
  </script>
  
  <style scoped>
  .calculadora-container {
    max-width: 300px;
    margin: 0 auto;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 8px;
    background-color: #f9f9f9;
    font-family: Arial, sans-serif;
  }
  
  h1 {
    text-align: center;
    color: #333;
    margin-bottom: 20px;
  }
  
  .resultado {
    background-color: white;
    border: 1px solid #ddd;
    border-radius: 4px;
    padding: 10px;
    margin-bottom: 15px;
    min-height: 30px;
    text-align: center;
  }
  
  .teclado {
    display: flex;
    flex-direction: column;
    gap: 10px;
  }
  
  .fila {
    display: flex;
    justify-content: center;
    gap: 10px;
  }
  
  .tecla {
    width: 60px;
    height: 60px;
    font-size: 24px;
    border: 1px solid #ccc;
    border-radius: 50%;
    background-color: #fff;
    cursor: pointer;
    transition: background-color 0.2s;
  }
  
  .tecla:hover {
    background-color: #e6e6e6;
  }
  
  .tecla:active {
    background-color: #d9d9d9;
  }
  </style>