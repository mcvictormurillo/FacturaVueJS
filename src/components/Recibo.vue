<template>
<div class="col-md-5 ">
<div class="card" style="width: 18rem;">
  <div class="card-body">
    <h5 class="card-title">RECIBO DE PAGO</h5>
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
     <div class="row">
        <div class="col-md-6">
            <h6 class="card-text text-left">Total:</h6>
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