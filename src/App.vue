<template>
  <div id="app">
   <h2 >Web Site Facturas</h2>
   <div class="container">
     <div class="row">
       <factura :compra="compra" :productoUnitario="productoUnitario" :descuento="descuento" :cantidad="cantidad" :subtotal="subtotal"></factura>
       <recibo :productoUnitario="productoUnitario" :descuento="descuento" :cantidad="cantidad" :subtotal="subtotal" :total="total"></recibo>
     </div>
     <div class="row">
       <table class="table mt-8">
            <thead class="thead-dark">
                <tr>
                <th scope="col">Ref</th>
                <th scope="col">Producto</th>
                <th scope="col">Precio</th>
                <th scope="col">Cantidad</th>
                <th scope="col">Descuento</th>
                <th scope="col">Subtotal</th>
                <th scope="col">Cliente</th>
                <th scope="col">Cedula</th>
                </tr>
            </thead>
            <tbody>
               <pedidos v-for="comp in compra" :key="comp.ref" :compra="comp"></pedidos> 
            </tbody>
        </table>
       
     </div>
   </div>    
  </div>
</template>

<script>

import factura from "./components/Factura.vue";
import Recibo from "./components/Recibo.vue";
import Pedidos from "./components/Pedidos.vue"
export default {
  name: 'App',
  data() {
    return {
      compra:[],
      descuento:10,
      cantidad:16,
      subtotal:9,
      total:17,

      productoUnitario:{
        ref:'00007',
        nombre:'mac',
        precio:'100000'
      }
    }
  },
  components: {
    factura,
    Recibo,
    Pedidos
  },

  
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.colors-example vs-input{
    margin: 5px;
    margin-top: 20px;
}
  
</style>
