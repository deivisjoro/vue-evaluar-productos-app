<script setup>
  import productos from './data';
  import Ficha from "./components/Ficha.vue";

  const aumentar = (index) => {
    productos.value[index].nota++;
    if(productos.value[index].nota>5)
      productos.value[index].nota = 1;
  }

  const disminuir = (index) => {
    productos.value[index].nota--;
    if(productos.value[index].nota<1)
      productos.value[index].nota = 5;

  }

</script>

<template>
  <div class="container">
    <h1>Evalua productos</h1>
    <div class="content">
      <Ficha 
        v-for="(producto, i) in productos" 
        :key="i" 
        :producto="producto" 
        :index="i" 
        @onAumentar="aumentar" 
        @onDisminuir="disminuir" 
      />
    </div>
  </div>
  
</template>

<style scoped>
  .container{
    width: 60%;
    margin-top: -50px;
  }

  h1{
    text-align: center;
    padding: 10px;
    background-color: #fff;
    margin-bottom: 10px;
    font-size: 18px;
    font-weight: bold;
    border-radius: 10px;
  }

  .content{
    border: 2px solid #666060;
    border-radius: 15px;
  }
</style>
