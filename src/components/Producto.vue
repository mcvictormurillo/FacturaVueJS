<template>
   <div class="card mb-3 mt-8" style="max-width: 50%; padding: 20px 20px">
       
        <div class="row no-gutters">
            <div class="col-md-5">
                <img class="card-img " :src="obtenerUrl" alt="">
            </div>
            <div class="col-md-7">
                <div class="card-body">
                <p class="card-text text-left">Nombre: {{nombreProducto}}</p>
                <p class="card-text text-left">Descripcion:{{descripcionProducto}} </p>
                <p class="card-title text-left">id: {{precioId}}</p>
   
                
            </div>
            </div>
        </div>
   </div>
</template>

<script>
import Productos from '../Data/Productos';

export default {
    name:'Producto',
    props:['nombreProducto','precio'],
    data() {
      return {
        
        nomProducto: this.nombreProducto,
        descripcionProducto: undefined,
        precioId: undefined

        
      }
    },
    
   
    computed:{
        obtenerUrl: function(){
            if(!this.nombreProducto){
                this.descripcionProducto = ''
                this.precioId = ''
                return "http://icons.iconarchive.com/icons/designbolts/free-multimedia/1024/Dslr-Camera-icon.png"
            }
            let imagen=undefined
            let n = Productos.productos.filter((p)=>{
                if(this.nombreProducto==p.nombre){
                    imagen = p.avatar
                    this.descripcionProducto = p.descripcion
                    return p.precio
                }
            })
            return imagen
        }
    }
}
</script>