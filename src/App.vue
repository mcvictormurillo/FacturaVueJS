<template>
  <div id="app">
   <h2 >Web Site Facturas</h2>
   <div class="container ">
     <div id="fac" class="row">
       <factura :compra="compra" :productoUnitario="productoUnitario" :descuento="descuento" :cantidad="cantidad" :subtotal="subtotal"></factura>
     </div>
     <div class="row">
       <table  class="table">
            <thead class="thead-dark">
                <tr>
                <th scope="col">Ref</th>
                <th scope="col">Producto</th>
                <th scope="col">Precio</th>
                <th scope="col">Cantidad</th>
                <th scope="col">Descuento</th>
                <th scope="col">Subtotal</th>
                <th scope="col"></th>
                </tr>
            </thead>
            <pedidos  :compra="compra" ></pedidos> 
            
        </table>
       
     </div>
   </div>    
  </div>
</template>

<script>

import factura from "./components/Factura.vue";

import Pedidos from "./components/Pedidos.vue"
export default {
  name: 'App',
  data() {
    return {
      compra:[],
      descuento:null,
      cantidad:null,
      subtotal:null,
      total:null,

      productoUnitario:{
        ref:null,
        nombre:null,
        precio:null
      }
    }
  },
 
  components: {
    factura,
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
#fac{
  margin-bottom: 20px;
}
</style>
