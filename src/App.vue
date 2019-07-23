<template>
  <v-app>
    <core-view />

    <core-footer />
  </v-app>
</template>

<script>

export default {
  name: 'App',
  components: {
    CoreFooter: () => import('@/components/core/Footer'),
    CoreView: () => import('@/components/core/View')
  },
  data () {
    return {
    //
    }
  }
}
</script>
