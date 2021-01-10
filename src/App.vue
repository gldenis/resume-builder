<template>
  <div class="container column">
    <app-form @submit="addBlock"></app-form>
    <app-content :blocks="blocks"></app-content>
  </div>
  <div class="container">
    <app-loader v-if="loading"></app-loader>
    <p v-else-if="comments.length === 0 && !loading">
      <button
        class="btn primary"
        @click="loadComments">Загрузить комментарии
      </button>
    </p>
    <comments-list
      v-else
      :comments="comments"></comments-list>
  </div>
</template>
<script>
import CommentsList from './components/CommentsList'
import AppLoader from './components/AppLoader'
import AppContent from './components/AppContent'
import axios from 'axios'
import AppForm from './components/AppForm'

export default {
  components: {
    AppForm,
    AppContent,
    AppLoader,
    CommentsList
  },
  data () {
    return {
      comments: [],

      blocks: [],
      loading: false
    }
  },
  mounted () {
    this.loadBlocks()
  },
  methods: {
    async loadComments () {
      try {
        this.loading = true
        const { data } =
            await
            axios.get(
              'https://jsonplaceholder.typicode.com/comments?_limit=10')

        this.comments = data
        this.loading = false
      } catch (e) {
        this.loading = false
      }
    },
    async loadBlocks () {
      try {
        const { data } = await
        axios.get(
          'https://resume-builder-be202-default-rtdb.firebaseio.com/blocks.json')

        this.blocks = Object.keys(data).map(key => {
          return {
            id: key,
            ...data[key]
          }
        })
      } catch (e) {

      }
    },
    async addBlock (block) {
      const { data } =
          await axios.post(
            'https://resume-builder-be202-default-rtdb.firebaseio.com/blocks.json',
            block)

      this.blocks.push({
        id: data.name,
        ...block
      })

      console.log(this.blocks)

      this.blockType = 'title'
      this.blockValue = ''
    }
  }
}
</script>
<style>
  .avatar {
    display: flex;
    justify-content: center;
  }

  .avatar img {
    width: 150px;
    height: auto;
    border-radius: 50%;
  }
</style>
