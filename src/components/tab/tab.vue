<template>
  <div class="tab">
    <cube-tab-bar
      :showSlider="true"
      v-model="selectedLabel"
      :data="tabs"
      ref="tabBar"
      class="border-bottom-1px"
    >
    </cube-tab-bar>
    <div class="slider-wrapper">
      <cube-slide
        :loop="false"
        :auto-play="false"
        :show-dots="false"
        :inital-index="index"
        ref="slide"
      >
        <cube-slide-item>
          <Goods></Goods>
        </cube-slide-item>
        <cube-slide-item>
          <Seller></Seller>
        </cube-slide-item>
        <cube-slide-item>
          <Ratings></Ratings>
        </cube-slide-item>
      </cube-slide>
    </div>
  </div>
</template>

<script>
  import Goods from 'components/goods/goods'
  import Seller from 'components/seller/seller'
  import Ratings from 'components/ratings/ratings'

  export default {
    name: 'tab',
    data () {
      return {
        index: 0,
        tabs: [{
          label: '商品'
        }, {
          label: '评价'
        }, {
          label: '商家'
        }]
      }
    },
    computed: {
      selectedLabel: {
        get () {
          return this.tabs[this.index].label
        },
        set (newVal) {
          this.index = this.tabs.findIndex((value) => {
            return value.label === newVal
          })
        }
      }
    },
    components: {
      Goods,
      Seller,
      Ratings
    }
  }
</script>

<style scoped lang="stylus">
  @import "~common/stylus/variable"
  .tab
    >>> .cube-tab
      padding: 10px 0
    display: flex
    flex-direction: column
    height: 100%
    .slider-wrapper
      flex: 1
      overflow: hidden
</style>
