<template>
  <div class="card">
    <div class="card-header alert alert-info">
      <span class="float-left">書名:{{book.title}}</span>
      <span class="float-right">價格:{{book.price}}</span>
    </div>
    <div class="card-block">
      <h4 class="card-title">簡介:</h4>
      <p>
        {{book.context}}
      </p>
      <div class="float-right">
        <button class="btn btn-info" @click="$emit('on-add',book)">
          <span v-show="!book.added">加入購物車</span>
          <span v-show="book.added">已購買</span>
        </button>
      </div> 
      <div class="clearfix"></div>
    </div>
  </div>
</template>
<style>
  .card-title,.card-title + p{
       text-align: left;
  }

  .card-title +p{
    padding: 0 15px 0 15px;
  }
  .card-block{
    padding-bottom: 10px
  }

  .alert{
    margin-bottom: 0px;
  }
</style>
<script>
export default {
  name: 'detail',
  props: ['book']
}
</script>
