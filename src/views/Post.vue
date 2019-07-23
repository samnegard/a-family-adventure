<template>
  <div id="post">
    <banner />

    <Article  />
  </div>
</template>

<script>
export default {
  name: 'Post',
  components: {
    Article: () => import('@/components/article/Article'),
    Banner: () => import('@/components/article/Banner')
  }
}
</script>
