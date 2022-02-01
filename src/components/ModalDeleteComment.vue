<template>
  <teleport to="#app">
    <!-- modal overlay -->
    <div :class="modalOpened ? 'block' : 'hidden'" class=" fixed z-1 bg-gray-500 bg-opacity-75 overflow-auto inset-0 w-full h-full grid place-items-center">
      <!-- modal content -->
      <div class="rounded-lg w-xs p-2rem bg-white">
        <div class="flex flex-col gap-4 justify-start">
          <h2 class="font-bold text-gray-700 ">
            Delete comment
          </h2>
          <p class="text-sm text-gray-500 ">
            Are you sure you want to delete this comment? This will remove the comment and can't be undone.
          </p>
          <div class="flex w-full gap-6 justify-self-stretch justify-between ">
            <button class="rounded-lg cursor-pointer font-medium bg-gray-500 text-white text-xs w-full py-2 px-2 uppercase" @click="$emit('close')">
              No, cancel
            </button>
            <button class="border rounded-lg cursor-pointer font-medium  bg-red-400 text-xs text-white w-full py-2 px-2 uppercase" @click="$emit('close')">
              Yes, Delete
            </button>
          </div>
        </div>
      </div>
    </div>
  </teleport>
</template>

<script setup lang='ts'>
defineProps<{ modalOpened: boolean }>()

defineEmits(['close'])

</script>

<style scoped>

</style>
