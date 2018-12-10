<template>
  <div class="tab">
    <cube-tab-bar
      :useTransition=false
      :showSlider=true
      v-model="selectedLabel"
      :data="tabs"
      ref="tabBar"
      class="border-bottom-1px"
    >
    </cube-tab-bar>
    <div class="slide-wrapper">
      <cube-slide
        :loop=false
        :auto-play=false
        :show-dots=false
        :initial-index="index"
        ref="slide"
      >
        <cube-slide-item>
          <goods></goods>
        </cube-slide-item>
        <cube-slide-item>
          <ratings></ratings>
        </cube-slide-item>
        <cube-slide-item>
          <seller></seller>
        </cube-slide-item>
      </cube-slide>
    </div>
  </div>
</template>

<script>
  import Goods from 'components/goods/goods'
  import Ratings from 'components/ratings/ratings'
  import Seller from 'components/seller/seller'

  export default {
    name: 'tab',
    props: {
      // tabs: {
      //   type: Array,
      //   default() {
      //     return []
      //   }
      // },
      initialIndex: {
        type: Number,
        default: 0
      }
    },
    data() {
      return {
        index: this.initialIndex,
        // slideOptions: {
        //   listenScroll: true,
        //   probeType: 3,
        //   directionLockThreshold: 0
        // }
        tabs: [
          {
            label: 'good'
          },{
            label: 'ratings'
          },{
            label: 'seller11'
          }
        ]
      }
    },
    computed: {
      selectedLabel: {
        get() {
          return this.tabs[this.index].label
        },
        set(newVal) {
          this.index = this.tabs.findIndex((value) => {
            return value.label === newVal
          })
        }
      }
    },
    mounted() {
      // this.onChange(this.index)
    },
    methods: {
      // onScroll(pos) {
      //   const tabBarWidth = this.$refs.tabBar.$el.clientWidth
      //   const slideWidth = this.$refs.slide.slide.scrollerWidth
      //   const transform = -pos.x / slideWidth * tabBarWidth
      //   this.$refs.tabBar.setSliderTransform(transform)
      // },
      // onChange(current) {
      //   this.index = current
      //   const instance = this.$refs.component[current]
      //   if (instance && instance.fetch) {
      //     instance.fetch()
      //   }
      // }
    },
    components: {
      Goods,
      Ratings,
      Seller
    }
  }
</script>

<style lang="stylus" scoped>
  @import "~common/stylus/variable"

  .tab
    display: flex
    flex-direction: column
    height: 100%
    >>> .cube-tab
      padding: 10px 0
    .slide-wrapper
      flex: 1
      overflow: hidden
</style>
