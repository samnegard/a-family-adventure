<template>
  <v-flex
    xs12
    :class="classes"
  >
    <base-card
      height="350"
      color="grey lighten-1"
      dark
    >
      <v-img
        :src="require(`@/assets/articles/${value.hero}`)"
        height="100%"
        gradient="rgba(0, 0, 0, .42), rgba(0, 0, 0, .42)"
      >
        <v-layout
          fill-height
          wrap
          text-xs-right
          ma-0
        >
          <v-flex xs12>
            <h3 class="title font-weight-bold mb-2">
              {{ value.title }}
            </h3>
          </v-flex>
          <v-flex align-self-end>
            <v-chip
              class="text-uppercase ma-0"
              color="primary"
              label
              small
              @click.stop="navigateTo()"
            >
              Read More
            </v-chip>
          </v-flex>
        </v-layout>
      </v-img>
    </base-card>
  </v-flex>
</template>

<script>
export default {
  props: {
    size: {
      type: Number,
      required: true
    },
    value: {
      type: Object,
      default: () => ({})
    }
  },

  methods: {
    navigateTo () {
      this.$vuetify.goTo(0)
      this.$router.push({ name: 'post', params: { id: this.value.title.replace(/\s+/g, '-').toLowerCase() } })
    }
  },

  computed: {
    classes () {
      return {
        'md6': this.size === 2,
        'md4': this.size === 3
      }
    }
  }
}
</script>

<style>
.v-image__image {
  transition: .3s linear;
}
</style>
