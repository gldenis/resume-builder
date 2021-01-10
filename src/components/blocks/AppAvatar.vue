<template>
  <div class="avatar">
    <img :src="blockValue">
  </div>
</template>
<script>
export default {
  name: 'AppAvatar',
  props: {
    blockValue: {
      type: String,
      required: true
    }
  }
}
</script>
<style scoped></style>
