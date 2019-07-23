<template>
  <section id="feed">
    <feed />
  </section>
</template>

<script>
export default {
  components: {
    Feed: () => import('@/components/Feed')
  }
}
</script>
