<template>
  <div v-for="comment in data?.results" :key="comment" class="grid p-1rem place-items-center">
    <comment-list-item :comment="comment" :vote="vote" @add-vote="vote++" @subtract-vote="vote--" />
  </div>

  <div v-for="comment in data?.results" :key="comment" class="grid p-1rem place-items-center">
    <comment-list-item :comment="comment" is-reply :vote="vote" is-me @add-vote="vote++" @subtract-vote="vote <= 0 ? 0 : vote--" />
  </div>

  <comment-editor />
</template>

<script setup lang='ts'>
import CommentEditor from './CommentEditor.vue'

const url = 'https://randomuser.me/api/?results=4'
const { data } = useFetch(url).json()
const vote = ref(0)

</script>
<style scoped>

</style>
