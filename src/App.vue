<template>
  <div id="app">
    <v-header :seller="seller"></v-header>
    <div class="tab-warpper">
      <tab></tab>
    </div>
  </div>
</template>

<script>
  import VHeader from './components/v-header/v-header'
  import { getSeller } from 'api'
  import Tab from 'components/tab/tab'

  export default {
    name: 'app',
    data () {
      return {
        seller: {}
      }
    },
    created () {
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
      Tab
    }
  }
</script>
<style lang="stylus">

</style>
