<template>
  <div
    class="card">
    <h2>Комментарии</h2>
    <ul v-if="comments.length" class="list">
      <li
        v-for="comment in comments"
        class="list-item"
        :key="comment.id">
        <div>
          <p><strong>{{ comment.email }}</strong></p>
          <small>{{ comment.body }}</small>
        </div>
      </li>
    </ul>
    <div v-else>Коментариев нету</div>
  </div>
</template>
<script>
export default {
  name: 'CommentsList',
  props: ['comments']
}
</script>
<style scoped></style>
