<template>
  <div class="p-1rem grid place-items-center">
    <div class="bg-white grid rounded-xl w-full max-w-3xl p-2rem gap-4 sm:flex sm:flex-shrink-0 sm:justify-between sm:items-start">
      <img
        class="rounded-full order-2 h-12 w-12
      col-span-2 inline-block sm:order-1"
        src="https://randomuser.me/api/portraits/thumb/men/75.jpg"
      >
      <textarea
        class=" border rounded-md border-gray-200 placeholder order-1 px-4 pt-2  pb-12  col-span-3 row-span-1 sm:flex-1 sm:order-2"
        placeholder="Add a comment..."
      />
      <button
        class="rounded-lg font-bold bg-indigo-700 order-3
     text-white tracking-wider col-end py-3 uppercase
     sm:order-3 sm:px-8"
      >
        send
      </button>
    </div>
  </div>
</template>

<script setup lang='ts'>

</script>

<style scoped>
input::-webkit-input-placeholder {
  transform:translateY(-30px)
}
</style>
