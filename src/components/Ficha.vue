<script setup>

    import estrella from '../assets/images/estrella.png';  
    
    const propiedades = defineProps({
        producto: Object,
        index: Number
    })

    const emisores = defineEmits(['onAumentar', 'onDisminuir']);

    const aumentar = () => {
        emisores('onAumentar', propiedades.index);
    }

    const disminuir = () => {
        emisores('onDisminuir', propiedades.index);
    }   

</script>

<template>
  <div class="producto">
    <div class="info">
        {{ producto.ropa }} ({{ producto.marca }})
    </div>
    <div class="opciones">
        <div class="estrellas">
            <span v-for="i in producto.nota" :key="i">
                <img :src="estrella" alt="imagen de estrella">
            </span>        
        </div>
        <div class="botones">
            <button @click="aumentar"> + </button>
            <button @click="disminuir"> - </button>
        </div>
    </div>
  </div>
  
</template>

<style scoped>

    .producto{
        display: flex;
        align-items: center;
        padding: 10px;
        border-bottom: 1px solid rgba(200, 200, 200, .5);
    }

    .info{
        flex: 1;
        background-color: #fff;
        padding: 5px;
        margin-right: 10px;
    }

    .opciones{
        flex: 1;
        display: flex;
        justify-content: space-between;
        align-items: center;
    }

    .estrellas img{
        width: 20px;
        margin: 1px;
    }

    .botones{
        display: flex;
    }

    button{
        display: flex;
        justify-content: center;
        align-items: center;
        width: 30px;
        height: 30px;
        margin: 0 5px;
        border-radius: 50%;
        font-size: 1.5em;
        font-weight: bold;
    }

    button:hover{
        cursor: pointer;
    }

</style>