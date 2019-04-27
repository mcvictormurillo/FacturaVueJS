<template>
<tbody>
  <tr v-for="(comp,index) in arrCompras" :key="comp.id">
        
        <td>{{comp.producto.nombre}}</td>
        <td>{{comp.producto.precio}}</td>
        <td>{{comp.cantidad}}</td>
        <td>{{comp.descuento}}</td>
        <td>{{comp.subtotal}}</td>
        <td><button @click="eliminarProducto(index)" class="btn btn-danger">Eliminar</button></td>
    </tr>
</tbody>
</template>

<script>

export default {
    name:'pedidos',
    props: ['compra','cantidad','descuento','subtotal','index'],
    data() {
        return {
            arrCompras : this.compra
        }
    },
    methods: {
        eliminarProducto:function(ind){
          this.arrCompras.splice(this.index,1)
        }
    },
}
</script>

