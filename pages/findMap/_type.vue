<template>
  <v-row no-gutters class="fill-height" style="width:100%">
    <!--  -->
    <MapComponent :finding="true" :pin="$route.query.type"></MapComponent>
  </v-row>
</template>

<script>
const MapComponent = () => import('~/components/MapComponent')
import { mapActions } from 'vuex'
export default {
  name: 'FindMap',
  head: {
    title: 'Указать адрес'
  },
  middleware: 'isProvider',
  components: {
    MapComponent
  },
  created() {
    this.setToolbar({
      header: '',
      toolbar: true
    })
  },
  beforeDestroy() {
    this.setToolbar()
  },
  methods: {
    ...mapActions('settings', ['setToolbar'])
  }
}
</script>

<style lang="scss" scoped>
</style>