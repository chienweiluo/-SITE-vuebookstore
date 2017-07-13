<template>
  <div class="hello" v-if="data.member">
    <nav class="navbar fixed-top bg-primary">
      <div class="navbar-brand">

        <price-count :total-price="data.member.totalPrice"></price-count>

        <span>
          <confirm @on-confirm="confirmPay"></confirm>
        </span>

        <span class="navbar-toggler-right">{{data.member.name}} 歡迎您</span>

      </div>
    </nav>

    <div class="container" id="book">
      <div class="row">
        <div class="col-md-12" v-for="book in data.books">
          <detail :book="book" @on-add="add" id="bookDetail"></detail>
        </div>
      </div>
    </div>

    <div class="fixed-area card">
      <book-count :total-number="data.member.totalNumber"></book-count>
    </div>
  </div>
</template>

<style>
  @import '../style/main.css';
</style>

<script>
import bookMarketService from '../bookMarketService'
import BookCount from './BookCount.vue'
import Detail from './Detail.vue'
import Confirm from './Confirm.vue'
import PriceCount from './PriceCount.vue'
export default {
  name: 'hello',
  components: {
    BookCount,
    Detail,
    Confirm,
    PriceCount
  },
  data () {
    return {
      data: {},
      goodTotal: 0
    }
  },
  methods: {
    get () {
      this.data = bookMarketService.get()
    },
    add (book) {
      book.added = !book.added
      this.data.member.totalPrice += book.added ? +book.price : -book.price
      this.data.member.totalNumber += book.added ? +1 : -1
    },
    confirmPay () {
      this.data.books.forEach((item) => { item.added = false })
      this.data.member.totalPrice = 0
      this.data.member.totalNumber = 0
    }
  },
  mounted () {
    this.get()
  }
}
</script>
