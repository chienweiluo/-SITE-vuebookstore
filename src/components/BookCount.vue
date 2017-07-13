<template>
  <div class="card-block">
    您已購入 <span>  {{totalNumber}} </span> 本書
  </div>
</template>

<style>
    .card-block::before{
        content: "";
        width: 0;
        height: 100%;
        display: inline-block;
        position: relative;
        vertical-align: middle;
        background: transparent;
    }
	.card-block span{
        font-size: 18px;
        display: inline-block;
        vertical-align: bottom;
	}
</style>
<script>
export default {
  name: 'bookCount',
  props: ['totalNumber']
}
</script>
