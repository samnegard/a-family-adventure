<template>
  <div>
    <v-toolbar
        absolute
        color="transparent"
        flat
        dark
      >
        <v-btn icon @click.stop="navigateHome()">
          <v-icon>mdi-home</v-icon>
        </v-btn>
        <v-toolbar-title>A Family Adventure</v-toolbar-title>
      </v-toolbar>
      <base-card dark>
        <v-img
          class="grey darken-2"
          height="300"
          width="100%"
          :src="require(`@/assets/articles/${article.hero}`)"
        >
          <v-layout
            fill-height
            align-center
            pa-3
          >
            <v-flex
              xs12
              md11
              offset-md1
            >
              <h1 class="display-3 font-weight-light">
                {{ article.title }}
              </h1>
            </v-flex>
          </v-layout>
        </v-img>
      </base-card>
  </div>
</template>

<script>
import {
  mapState
} from 'vuex'

export default {
  computed: {
    ...mapState(['articles']),
    article () {
      return this.articles.find(a => a.title.replace(/\s+/g, '-').toLowerCase() === this.$route.params.id)
    }
  },

  methods: {
    navigateHome () {
      this.$router.push({ name: 'home' })
    }
  }
}
</script>
