<template>
  <div>
    <span class="navbar-toggler-left">結帳金額為:{{totalPrice}}</span>
  </div>
</template>

<script>
export default {
  name: 'priceCount',
  props: ['totalPrice']
}
</script>
