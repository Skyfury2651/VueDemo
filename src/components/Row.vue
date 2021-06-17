<template>
  <li @click="emitParent">
    Child id {{ post.id }} : title {{ post.title }}
  </li>
</template>

<script>
export default {
  name: "Row",
  props: ['post'],
  methods: {
    emitParent() {
      return this.$emit('handler', this.post.id)
    }
  }
}
</script>

<style scoped>

</style>