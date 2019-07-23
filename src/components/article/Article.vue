<template>
  <div id="article">
    <v-container
      id='article-content'
      tag='section'
    >
      <v-layout wrap>
        <v-dialog
          v-model="dialog"
          max-width="1200"
        >
          <v-card v-if="selectedImage">
            <v-img
              :src="require(`@/assets/articles/${selectedImage}`)"
              class="grey lighten-2"
            >
            </v-img>
          </v-card>
        </v-dialog>
        <div class="my-4">
          <v-flex xs12 lg8 offset-lg2>
            <p style="white-space: pre-wrap;">{{ article.text }}</p>
          </v-flex>
          <v-flex xs12 lg8 offset-lg2>
            <v-card flat color="transparent">
              <v-container grid-list-sm fluid>
                <v-layout row wrap>
                  <v-flex
                    v-for="(image, n) in article.images"
                    :key="n"
                    xs4
                    d-flex
                  >
                    <v-card flat tile class="d-flex">
                      <v-img
                        :src="require(`@/assets/articles/${image}`)"
                        :lazy-src="`https://picsum.photos/10/6?image=${n * 5 + 10}`"
                        aspect-ratio="1"
                        class="grey lighten-2"
                        @click="zoom(`${image}`)"
                      >
                        <template v-slot:placeholder>
                          <v-layout
                            fill-height
                            align-center
                            justify-center
                            ma-0
                          >
                            <v-progress-circular indeterminate color="grey lighten-5"></v-progress-circular>
                          </v-layout>
                        </template>
                      </v-img>
                    </v-card>
                  </v-flex>
                </v-layout>
              </v-container>
            </v-card>
          </v-flex>
        </div>
      </v-layout>
    </v-container>
  </div>
</template>

<script>
import {
  mapState
} from 'vuex'

export default {
  data () {
    return {
      selectedImage: null,
      dialog: false
    }
  },

  computed: {
    ...mapState(['articles']),
    article () {
      return this.articles.find(a => a.title.replace(/\s+/g, '-').toLowerCase() === this.$route.params.id)
    }
  },

  methods: {
    zoom (url) {
      this.dialog = true
      this.selectedImage = url
    }
  }
}
</script>
