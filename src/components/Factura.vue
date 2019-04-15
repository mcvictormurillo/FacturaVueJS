<template>


  <form  @submit.prevent="AddProducto"  class="needs-validation col-7" novalidate>
  <div class="form-row">
    <div class="col-md-4 mb-3">
      <label for="validationCustom01">Ref</label>
      <input v-model="productoUnitario.ref" type="text" class="form-control" placeholder="0-000001">
    </div>
    <div class="col-md-8 mb-3">
      <label for="validationCustom01">Nombre Producto</label>
      <input v-model="productoUnitario.nombre" type="text" class="form-control" placeholder="Nombre">
    </div>

    <div class="col-md-4 mb-3">
      <label for="validationCustom02">Precio</label>
      <input v-model="productoUnitario.precio" type="number" class="form-control" placeholder="$0" value="Otto" required>
    </div>
    <div class="col-md-8 mb-3">
      <label for="validationCustom01">Descuento</label>
      <input v-model="des" type="text" class="form-control" placeholder="0">
    </div>

     <div class="col-md-4 mb-3">
      <label for="validationCustom02">Cantdiad</label>
      <input v-model="cantidad" type="number" class="form-control" placeholder="0" value="Otto" required>
    </div>
    <div class="col-md-8 mb-3">
      <label for="validationCustom01">SubTotal</label>
      <input v-model="subtotal" type="text" class="form-control" placeholder="$0">
    </div>
</div>
    
  <button  class="btn btn-info" type="submit">Agregar Producto</button>
  <button class="btn btn-success" type="submit">Terminar Pedido</button>
</form>





</template>

<script>

export default {

    name:'factura',
    data() {
      return {
        des: this.descuento
      }
    },
    props:['productoUnitario','descuento','cantidad','subtotal','compra'],
    methods: {
      
      AddProducto: function(){
        self = this
       
        var productToAdd = {
          ref: self.productoUnitario.ref,
          nombre: self.productoUnitario.nombre,
          precio: self.productoUnitario.precio,
        }
        let objCompra={
          cantidad: self.cantidad,
          descuento: self.descuento,
          subtotal: self.subtotal,
          producto: productToAdd
        }
        self.compra.push(objCompra)
        console.log(this.compra)
      }

    },
   
}
</script>