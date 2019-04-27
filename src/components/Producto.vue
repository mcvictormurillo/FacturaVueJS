<template>
   <div class="card mb-3 mt-8" style="max-width: 50%; padding: 20px 20px">
       
        <div class="row no-gutters">
            <div class="col-md-5">
                <img class="card-img " :src="obtenerUrl" alt="">
            </div>
            <div class="col-md-7">
                <div class="card-body">
                <h5 class="card-title">id: {{this.index}}</h5>
                <p class="card-text">Precio:</p>
                <p class="card-text">Nombre:</p>
                
            </div>
            </div>
        </div>
   </div>
</template>

<script>

import Productos from '../Data/Productos';
export default {
    name:'Producto',
    props:['index'],
    data() {
      return {
        indexLista :  this.index,
        

      }
    },
   
    computed:{
        obtenerUrl: function(){
            if(!this.index){
                return "https://livearn.io/themes/wowonder/img/publisher/gallery.svg"
            }else{
                return  Productos.productos[this.index].avatar
            }   
        }
    }
}

</script>
