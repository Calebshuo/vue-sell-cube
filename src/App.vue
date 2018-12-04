<template>
  <div id="app">
    <v-header :seller="seller"></v-header>
  </div>
</template>

<script>
import { getSeller } from 'api'
import VHeader from 'components/v-header/v-header'

export default {
  data() {
    return {
      seller: {}
    }
  },
  name: 'app',
  created() {
    getSeller().then((seller) => {
      this.seller = seller
    })
  },
  components: {
    VHeader
  }
}
</script>
<style lang="stylus">

</style>
