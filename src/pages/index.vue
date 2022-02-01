<script setup lang="ts">
import { isDark, toggleDark } from '~/composables/dark'
import CommentList from '~/components/CommentList.vue'

</script>

<template>
  <button @click="toggleDark()">
    <carbon-sun v-if="!isDark" />
    <carbon-moon v-if="isDark" :class="isDark && 'text-white'" />
  </button>
  <CommentList />
</template>
