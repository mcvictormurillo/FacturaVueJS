<template>

<div class="row">
  <form  @submit.prevent="AddProducto"  class="needs-validation col-5" novalidate>
  <div class=" form-row">
    <div class="col-md-12 mb-3 text-left">
      <label for="validationCustom01">Cliente</label>
      <input v-model="cliente.nombre" type="text" class="form-control" placeholder="Nombre del cliente">
    </div>
    <div class="col-md-12 mb-3 text-left">
      <label for="validationCustom01">Identificacion</label>
      <input v-model="cliente.id" type="text" class="form-control" placeholder="CC.">
    </div>
    <div class="col-md-12 mb-3 text-left">
      <label for="validationCustom01">Celular</label>
      <input v-model="cliente.celular" type="text" class="form-control" placeholder="000-000-0000">
    </div>
    <!--<div class="col-md-4 mb-3 text-left">
      <label for="validationCustom01">Ref</label>
      <input   v-model="producto.ref" type="text" class="form-control" placeholder="0-000001">
    </div> -->
    <div class="col-md-12 mb-3 text-left">
      <label for="sel">Nombre Producto</label>
      <select v-bind:value="producto.nombre" v-on:change="producto.nombre = $event.target.value" class="form-control" id="sel">
        <option id="0" value="Iphone 5">Iphone 5</option>
        <option id="1" value="Iphone 6">Iphone 6</option>
        <option id="2" value="Iphone 7">Iphone 7</option>
        <option id="3" value="Iphone 8">Iphone 8</option>
        <option id="4" value="Macbook Pro">Macbook Pro</option>
        <option id="5" value="Macbook Air">Macbook Air</option>
        <option id="6" value="Smart TV">Smart TV</option>
        <option id="7" value="Audifonos">Audifonos</option>
        <option id="8" value="Teclado">Teclado</option>
        <option id="9" value="Mouse">Mouse</option>
      </select>
      
    </div>

    <div class="col-md-4 mb-3 text-left">
      <label for="validationCustom02">Precio</label>
      <input v-model="producto.precio" type="number" class="form-control" placeholder="$0" value="Otto" required>
    </div>
    <div class="col-md-8 mb-3 text-left">
      <label for="validationCustom01">Descuento %</label>
      <input v-model="des" type="text" class="form-control" placeholder="0">
    </div>

     <div class="col-md-4 mb-3 text-left">
      <label for="validationCustom02">Cantdiad</label>
      <input  v-model="cant" type="number" class="form-control" placeholder="0" value="Otto" required>
    </div>
    <div class="col-md-8 mb-3 text-left">
      <label for="validationCustom01">SubTotal</label>
      <input v-model="calcularSubtotal" type="text" class="form-control" placeholder="$0" disabled>
    </div>
</div>
    
  <button  class="btn btn-info">Agregar Producto</button>
  
</form>

<!--
  <recibo :productoUnitario="producto" :descuento="des" :cantidad="cant" :subtotal="calcularSubtotal" :total="total"></recibo>

  -->
<Producto :nombreProducto="producto.nombre" :precio="producto.precio"/>
</div>


</template>

<script>
import Recibo from "./Recibo.vue";
import Producto from './Producto.vue'
import Productos from '../Data/Productos.js'

export default {

    name:'factura',
    props:['productoUnitario','descuento','cantidad','subtotal','compra','total','cliente'],
    data() {
      return {
        des: this.descuento,
        cant: this.cantidad,
        subto: this.subtotal,
        producto: this.productoUnitario,
        
      }
    },
    methods:{
      calcular: function(){
        this.subto = parseFloat(this.producto.precio) * parseFloat(this.cantidad)
        console.log(subto)
      }
      
     
    },
    components:{
      Recibo
    },
    computed:{
      calcularSubtotal: function(){
        if(this.cant!='' && this.producto.precio!=''){
          let varloProducto = this.producto.precio - this.producto.precio*this.des/100
          return this.cant * varloProducto
        }else{
          return 0
        }
        
      }

    },
    methods: {
      
      AddProducto: function(){
        self = this
        
        
        var productToAdd = {
          ref: self.producto.ref,
          nombre: self.producto.nombre,
          precio: self.producto.precio,
        }
        let objCompra={
          id: new Date().getTime(),
          cantidad: self.cant,
          descuento: self.des,
          subtotal: this.calcularSubtotal,
          producto: productToAdd
        }
        
        //if(objCompra.producto.nombre!=null && objCompra.subtotal!=0){
          self.compra.push(objCompra)
          //limpiar 
          
          this.des = ''
          this.cant = ''
          this.subto = ''
          this.producto.ref = ''
          this.producto.nombre = ''
          this.producto.precio = ''
          
       // }
        

      }

    },
    components:{
      Producto
    }
   
}
</script>