<template>
  <base-card dark>
    <v-img
      class="grey darken-2"
      height="500"
      width="100%"
      :src="require('@/assets/articles/banner.jpg')"
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
            A Family Adventure
          </h1>
          <div class="subheading text-uppercase pl-2 mb-4">
            Taking it From Armidale, one step at a time
          </div>
        </v-flex>
      </v-layout>
    </v-img>
  </base-card>
</template>
