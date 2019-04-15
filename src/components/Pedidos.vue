<template>
   <tr>
        <td>{{compra.ref}}</td>
        <td>{{compra.nombre}}</td>
     </tr>
</template>

<script>

export default {
    name:'pedidos',
    props: ['compra']
}
</script>