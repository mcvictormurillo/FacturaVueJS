<template>
  <div id="app">
   <h2 >Web Site Facturas</h2>
   <div class="container ">
     <div id="fac" class="row">
       <factura :compra="compra" :productoUnitario="productoUnitario" 
       :descuento="descuento" :cantidad="cantidad" 
       :subtotal="subtotal" :total="calcularTotal" 
       :cliente="cliente"></factura>
       
       
     </div>
     <div class="row">
       
       <div class="col-12 card" >
         
         <div class="row " style="margin-top: 24px">
           <div class="col-4" >
           <h6 class="text-left">Numero:<small> {{fecha.getTime()}}</small></h6>
           <h6 class="text-left">Fecha Venta:<small> {{fecha}}</small></h6>
           <h6 class="text-left">Fecha Vencimiento</h6>
           <h3 class="text-left">Total es $ {{calcularTotal}}</h3>
         </div>

         <div class="col-4">
           <h6 class="text-left">Cliente: <small>{{cliente.nombre}}</small></h6>
           <h6 class="text-left">Id:<small> {{cliente.id}}</small></h6>
           <h6 class="text-left">Celular: <small>{{cliente.celular}}</small></h6>
        

         </div>
         <div class="col-4" >
           <h1 class="text-right">Factura</h1>
           <p class="text-right">Quillet, S.A</p>
           <p class="text-right">Autovia 8km</p>
           <p class="text-right">info@quillet.com</p>
         </div>
         </div>

        <div class="row">
           <div class="col-12">
           <table  class="table table-striped table-bordered table-hover table-sm">
            <thead class="thead-light">
                <tr>
                
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
       
     </div>
   </div>    
  </div>
</template>

<script>

import factura from "./components/Factura.vue";
import Pedidos from "./components/Pedidos.vue";

export default {
  name: 'App',
  data() {
    return {
      fecha: new Date(),
      //fechaV: new Date(1997,fecha.getMonth(),1),
      compra:[],
      descuento:null,
      cantidad:null,
      subtotal:null,
      total:this.calcularTotal,
      cliente:{
        nombre:undefined,
        id:undefined,
        celular:undefined,
      },
      productoUnitario:{
        ref:null,
        nombre:null,
        precio:null
      }
    }
  },
  computed:{
      calcularTotal: function(){
        
          let sumatoria= 0
          this.compra.forEach(element => {
            sumatoria += parseFloat(element.subtotal)
          });
          console.log(`el total es ${sumatoria}`)
          console.log(this.compra)
        return sumatoria
      }
      

  },
  methods:{
    calTotal: function(){
      console.log(`Esta es la compra: ${this.compra}`)
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
.card{
-webkit-box-shadow: 7px 7px 5px 0px rgba(204,204,204,0.9);
-moz-box-shadow: 7px 7px 5px 0px rgba(204,204,204,0.9);
box-shadow: 7px 7px 5px 0px rgba(204,204,204,0.9);
}
thead{
  background: #ffffff;
}
</style>
