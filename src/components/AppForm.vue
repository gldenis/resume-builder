<template>
  <form
    class="card card-w30"
    @submit.prevent="submitHandler">
    <div class="form-control">
      <label for="type">Тип блока</label>
      <select
        id="type"
        v-model="blockType">
        <option value="title">Заголовок</option>
        <option value="subtitle">Подзаголовок</option>
        <option value="avatar">Аватар</option>
        <option value="text">Текст</option>
      </select>
    </div>
    <div class="form-control">
      <label for="value">Значение</label> <textarea
      v-model="blockValue"
      id="value"
      rows="3"></textarea>
    </div>
    <button
      :disabled="disabledBtn"
      type="submit"
      class="btn primary">Добавить
    </button>
  </form>
</template>
<script>
export default {
  name: 'AppForm',
  emits: {
    submit (block) {
      return ['title', 'subtitle', 'avatar', 'text'].includes(block.blockType) &&
          block.blockValue.length > 3
    }
  },
  data () {
    return {
      blockType: 'title',
      blockValue: ''
    }
  },
  computed: {
    disabledBtn () {
      return this.blockValue.trim().length < 4
    }
  },
  methods: {
    submitHandler () {
      this.$emit('submit', {
        blockType: this.blockType,
        blockValue: this.blockValue
      })
      this.blockType = 'title'
      this.blockValue = ''
    }
  }
}
</script>
<style scoped></style>
