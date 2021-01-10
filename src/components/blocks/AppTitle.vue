<template>
  <h1>{{ blockValue }}</h1>
</template>
<script>
export default {
  name: 'AppTitle',
  props: {
    blockValue: {
      type: String,
      required: true
    }
  },
  mounted () {
    console.log(this.$attrs)
  }
}
</script>
<style scoped></style>
