<template>
  <h2>{{ blockValue }}</h2>
</template>
<script>
export default {
  name: 'AppSubtitle',
  props: {
    blockValue: {
      type: String,
      required: true
    }
  }
}
</script>
<style scoped></style>
