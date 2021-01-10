<template>
  <p>{{ blockValue }}</p>
</template>
<script>
export default {
  name: 'AppText',
  props: {
    blockValue: {
      type: String,
      required: true
    }
  }
}
</script>
<style scoped></style>
