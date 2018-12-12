<template>
  <div id="app">
    <v-header :seller="seller"></v-header>
    <div class="tab-wrapper">
      <tab :tabs="tabs"></tab>
    </div>
  </div>
</template>

<script>
import { getSeller } from 'api'
import VHeader from 'components/v-header/v-header'
import tab from 'components/tab/tab'
import Goods from 'components/goods/goods'
import Ratings from 'components/ratings/ratings'
import Seller from 'components/seller/seller'

export default {
  data() {
    return {
      seller: {
        type: Object,
        default: {}
      }
    }
  },
  computed: {
    tabs() {
      return [
          {
            label: '商品',
            component: Goods,
            data: this.seller
          },
          {
            label: '评论',
            component: Ratings,
            data: this.seller
          },
          {
            label: '商家',
            component: Seller,
            data: this.seller
          }
        ]
    }
  },
  created() {
    this._getSeller()
  },
  methods: {
    _getSeller() {
      getSeller().then((seller) => {
      this.seller = seller
    })
   }
  },
  components: {
    VHeader,
    tab
  }
}
</script>
<style lang="stylus">
  #app
    .tab-wrapper
      position: fixed 
      top: 136px
      left: 0
      right: 0
      bottom: 0
</style>
