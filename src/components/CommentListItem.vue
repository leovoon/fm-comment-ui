<template>
  <div v-if="isMediumScreen" :class="isReply ? 'ml-16 max-w-[44rem]' : 'max-w-3xl' " class="bg-white rounded-xl relative flex p-2rem">
    <span v-if="isReply" class="bg-gray-200 h-[calc(100%+2rem)]  -inset-x-6 -top-2rem w-[2.5px] absolute" />
    <div class="flex flex-col mr-2rem items-center justify-start">
      <button class="rounded-t-xl flex bg-gray-100   py-3 px-4 text-gray-400 items-center " @click="vote++">
        <carbon-add />
      </button>
      <span class="font-bold bg-gray-100 text-lg text-center w-full   text-indigo-700">{{ vote }}</span>
      <button class="rounded-b-xl flex bg-gray-100   py-3 px-4 text-gray-400 items-center " @click="vote++">
        <carbon:subtract class="inline-block" />
      </button>
    </div>
    <div class="flex flex-col mb-1rem w-full gap-4 justify-start  ">
      <div class="flex justify-between">
        <div class="inline-flex items-center justify-center gap-4">
          <img class="rounded-full" :src="comment.picture.thumbnail">
          <span class="font-bold">
            {{ comment.login.username }}
          </span>
          <div v-if="isMe" class="rounded-sm font-semibold bg-indigo-700 text-white px-2 pb-1 leading-5 table-cell align-middle">
            <span>
              you
            </span>
          </div>
          <span class="font-normal text-gray-400">1 month ago</span>
        </div>
        <template v-if="isMe">
          <div class="flex gap-4">
            <button class="flex font-medium text-red-500 gap-1 items-center" @click="openModal">
              <carbon-trash-can /> Delete
            </button>
            <button class="flex font-medium text-indigo-700 gap-1 items-center">
              <carbon-edit />
              Edit
            </button>
          </div>
        </template>

        <template v-else>
          <button class="flex font-bold text-indigo-700 gap-2 items-center ">
            <carbon-reply />
            <div class="tracking-wider">
              Reply
            </div>
          </button>
        </template>
      </div>

      <p class="text-gray-500">
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Corporis eveniet natus distinctio perferendis perspiciatis aliquam. Voluptatibus unde eligendi architecto error delectus pariatur iste veritatis nemo obcaecati impedit! Hic, quo nisi.
      </p>
    </div>
  </div>
  <!-- mobile  -->
  <div
    v-else :class="isReply && 'ml-10' " class="bg-white
  rounded-xl min-w-sm p-2rem relative "
  >
    <span v-if="isReply" class="bg-gray-200 h-[calc(100%+2rem)]  -inset-x-6 -top-2rem w-[2.5px] absolute" />

    <div class="flex flex-wrap mb-1rem gap-4 items-center justify-start ">
      <img class="rounded-full" :src="comment.picture.thumbnail">
      <div class="font-bold">
        {{ comment.login.username }}
      </div>
      <div v-if="isMe" class="rounded-sm font-semibold bg-indigo-700 text-white px-2 pb-1 leading-5 table-cell align-middle">
        <span>
          you
        </span>
      </div>
      <span class="font-normal text-gray-400">1 month ago</span>
    </div>
    <p class="text-gray-600">
      ipsum dolor, sit amet consectetur adipisicing elit. Tempora quos laboriosam eligendi consequuntur blanditiis, reiciendis deserunt perspiciatis. Consequatur ex culpa voluptas commodi numquam enim perspiciatis dolore cum? Fugiat, architecto cumque!
    </p>
    <div class="flex mt-1rem w-full items-center justify-between">
      <div class="rounded-l-xl rounded-r-xl flex bg-gray-200 items-center">
        <button class="flex py-3 px-4 text-gray-400 items-center " @click="$emit('addVote')">
          <carbon-add />
        </button>
        <span class="font-bold text-lg text-indigo-700">{{ vote }}</span>
        <button class="flex py-3 px-4 text-gray-400 items-center " @click="$emit('subtractVote')">
          <carbon:subtract class="inline-block" />
        </button>
      </div>
      <template v-if="isMe">
        <div class="flex gap-4">
          <button class="flex font-medium text-red-500 gap-1 items-center" @click="openModal">
            <carbon-trash-can /> Delete
          </button>
          <button class="flex font-medium text-indigo-700 gap-1 items-center">
            <carbon-edit />
            Edit
          </button>
        </div>
      </template>
      <template v-else>
        <button class="flex font-bold text-indigo-700 gap-2 items-center ">
          <carbon-reply />
          <div class="tracking-wider">
            Reply
          </div>
        </button>
      </template>
    </div>
  </div>

  <modal-delete-comment :modal-opened="showModal" @close="handleModalClose" />
</template>

<script setup lang='ts'>

interface Comment {
  picture: {
    thumbnail: string
  }
  login: {
    username: string
  }
}

interface Props {
  comment: Comment
  vote: number
  isMe?: boolean
  isReply?: boolean
}

const props = withDefaults(defineProps<Props>(), {
  vote: 0,
})

defineEmits(['addVote', 'subtractVote'])

const vote = computed(() => props.vote)

const isMediumScreen = useMediaQuery('(min-width: 768px)')
const showModal = ref(false)
const openModal = () => showModal.value = true
const handleModalClose = () => showModal.value = false

</script>
