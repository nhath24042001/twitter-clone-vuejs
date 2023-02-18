<script lang="ts">
import { defineComponent } from "vue";
import HeartOutline from "vue-material-design-icons/HeartOutline.vue";
import ChartBar from "vue-material-design-icons/ChartBar.vue";
import MessageOutline from "vue-material-design-icons/MessageOutline.vue";
import Sync from "vue-material-design-icons/Sync.vue";
import DotsHorizontal from "vue-material-design-icons/DotsHorizontal.vue";
import TrashCanOutline from "vue-material-design-icons/TrashCanOutline.vue";

export default defineComponent({
  data() {
    return {
      openOptions: false,
      tweetImg: null,
    };
  },
  methods: {
    randomItem(items: string | any) {
      return items[Math.floor(Math.random() * items.length)];
    },
  },
  props: {
    tweet: Object,
  },
  components: {
        DotsHorizontal
},
});
</script>

<template>
  <div class="min-w-[60px]">
    <img
      src="https://images.unsplash.com/photo-1670272498425-e13ce4fcf5f0?ixlib=rb-4.0.3&ixid=MnwxMjA3fDF8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=870&q=80"
      alt="tweet_img"
      class="rounded-full m-2 mt-3"
      width="50"
      height="50"
    />
  </div>

  <div class="p-2 w-full">
    <div class="font-extrabold flex items-center justify-between mt-0.5 mb-1.5">
      <div class="flex items-center">
        <div class="">{{ tweet?.name }}</div>
        <span class="font-[300] text-[15px] text-gray-500 pl-2">{{
          tweet?.handle
        }}</span>
      </div>

      <div class="hover:bg-gray-800 rounded-full cursor-pointer ralative">
        <button type="button" class="block p-2">
          <DotsHorizontal @click="openOptions = !openOptions" />
        </button>
      </div>
    </div>

    <div class="pb-3">{{ tweet?.tweet }}</div>
    <div v-if="tweet?.file">
        <div v-if="!tweet?.is_Video" class="rounded-xl">
            <img 
            :src="tweet.file" 
            alt="img"
            class="mt-2 object-fill rounded-xl w-full"
            >
        </div>
        <div v-else>
            <video :src="tweet.file" class="rounded-xl" controls></video>
        </div>
    </div>
  </div>
</template>
