<template>
<div class="col-md-7 ">
<div class="card" >
  <div class="card-body">
    <div class="row mb-8">
        <div class="col-3 text-left">
            <img class="mb-8" src="../assets/analytics.png">
        </div>
        <div class="col-9">
            <h3 class="card-title text-left">FACTURA</h3>
        </div>
    </div>
    <div class="row">
        <div class="col-md-6">
            <h6 class="card-text text-left">Ref:</h6>
        </div>
        <div class="col-md-6">
            <p class="text-muted text-right">{{productoUnitario.ref}}</p>
        </div>
    </div>
      <div class="row">
        <div class="col-md-6">
            <h6 class="card-text text-left">Producto:</h6>
        </div>
        <div class="col-md-6">
            <p class="text-muted text-right">{{productoUnitario.nombre}}</p>
        </div>
    </div>
    <div class="row">
        <div class="col-md-6">
            <h6 class="card-text text-left">Precio:</h6>
        </div>
        <div class="col-md-6">
            <p class="text-muted text-right">{{productoUnitario.precio}}</p>
        </div>
    </div>
    <div class="row">
        <div class="col-md-6">
            <h6 class="card-text text-left">Cantidad:</h6>
        </div>
        <div class="col-md-6">
            <p class="text-muted text-right">{{cantidad}}</p>
        </div>
    </div>
    <div class="row">
        <div class="col-md-6">
            <h6 class="card-text text-left">Descuento</h6>
        </div>
        <div class="col-md-6">
            <p class="text-muted text-right">{{descuento}}</p>
        </div>
    </div>
    <div class="row">
        <div class="col-md-6">
            <h6 class="card-text text-left">Subtotal:</h6>
        </div>
        <div class="col-md-6">
            <p class="text-muted text-right">{{subtotal}}</p>
        </div>
    </div>
     <div class="row mt-8">
        <div class="col-md-6 mt-8">
            <h4 class="card-text text-left">Total:</h4>
        </div>
        <div class="col-md-6">
            <p class="text-muted text-right">{{total}}</p>
        </div>
    </div>

  </div>
</div>
</div>
</template>

<script>
export default {
    name:'recibo',
    props:['productoUnitario','descuento','cantidad','subtotal','total']
}
</script>