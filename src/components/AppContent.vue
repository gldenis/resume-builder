<template>
  <div class="card card-w70">
    <h3 v-if="blocks.length === 0">
      Добавьте первый блок, чтобы увидеть результат </h3>
    <template v-else>
      <template
        v-for="block in blocks"
        :key="block.id">
        <component
          :block-value="block.blockValue"
          v-bind="{ blockValue: block.blockValue }"
          :is="'app-' + block.blockType"></component>
      </template>
    </template>
  </div>
</template>
<script>
import AppTitle from './blocks/AppTitle'
import AppSubtitle from './blocks/AppSubtitle'
import AppText from './blocks/AppText'
import AppAvatar from './blocks/AppAvatar'

export default {
  name: 'AppContent',
  components: {
    AppTitle,
    AppSubtitle,
    AppText,
    AppAvatar
  },
  props: {
    blocks: {
      type: Array,
      required: false,
      default () {
        return []
      }
    }
  }
}
</script>
<style scoped></style>
