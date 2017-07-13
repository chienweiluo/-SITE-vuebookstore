<template>
  <div>
    <button class="btn btn-primary" @click="$emit('on-confirm')">確定結帳</button>
  </div>
</template>

<script>
export default {
  name: 'confirm'
}
</script>
