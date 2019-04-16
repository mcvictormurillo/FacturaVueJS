<template>

<div class="row">
  <form  @submit.prevent="AddProducto"  class="needs-validation col-7" novalidate>
  <div class="form-row">
    <div class="col-md-4 mb-3">
      <label for="validationCustom01">Ref</label>
      <input v-model="producto.ref" type="text" class="form-control" placeholder="0-000001">
    </div>
    <div class="col-md-8 mb-3">
      <label for="validationCustom01">Nombre Producto</label>
      <input v-model="producto.nombre" type="text" class="form-control" placeholder="Nombre">
    </div>

    <div class="col-md-4 mb-3">
      <label for="validationCustom02">Precio</label>
      <input v-model="producto.precio" type="number" class="form-control" placeholder="$0" value="Otto" required>
    </div>
    <div class="col-md-8 mb-3">
      <label for="validationCustom01">Descuento %</label>
      <input v-model="des" type="text" class="form-control" placeholder="0">
    </div>

     <div class="col-md-4 mb-3">
      <label for="validationCustom02">Cantdiad</label>
      <input  v-model="cant" type="number" class="form-control" placeholder="0" value="Otto" required>
    </div>
    <div class="col-md-8 mb-3">
      <label for="validationCustom01">SubTotal</label>
      <input v-model="calcularSubtotal" type="text" class="form-control" placeholder="$0" disabled>
    </div>
</div>
    
  <button  class="btn btn-info">Agregar Producto</button>
  
</form>


<recibo :productoUnitario="producto" :descuento="des" :cantidad="cant" :subtotal="calcularSubtotal" :total="calcularTotal"></recibo>

</div>


</template>

<script>
import Recibo from "./Recibo.vue";


export default {

    name:'factura',
    props:['productoUnitario','descuento','cantidad','subtotal','compra'],
    data() {
      return {
        des: this.descuento,
        cant: this.cantidad,
        subto: this.subtotal,
        producto: this.productoUnitario
      }
    },
    methods:{
      calcular: function(){
        this.subto = parseFloat(this.producto.precio) * parseFloat(this.cantidad)
        console.log(subto)
      },
     
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
        
      },
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
   
}
</script>