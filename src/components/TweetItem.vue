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
        DotsHorizontal,
        MessageOutline,
        Sync,
        HeartOutline,
        ChartBar

},
});
</script>

<template>
  <div v-if="tweet?.avatar_img" class="min-w-[60px]">
    <img
      :src="tweet.avatar_img"
      alt="tweet_img"
      class="w-[60px] h-[60px] rounded-full m-2 mt-3"
    />
  </div>

  <div class="p-2 w-full">
    <div class="font-extrabold flex items-center justify-between mt-0.5 mb-1.5">
      <div class="flex items-center">
        <div class="">{{ tweet?.name }}</div>
        <span class="font-[300] text-[15px] text-gray-500 pl-2">{{
          tweet?.handle
        }}</span>
        <span class="font-[300] text-[15px] text-gray-500 pl-2">{{tweet?.time}}</span>
      </div>

      <div class="hover:bg-gray-800 rounded-full cursor-pointer ralative">
        <button type="button" class="block p-2">
          <DotsHorizontal @click="openOptions = !openOptions" />
        </button>
      </div>
    </div>

    <div class="pb-3 w-[85%]">{{ tweet?.tweet }}</div>
    <div v-if="tweet?.img">
        <div v-if="!tweet?.is_Video" class="rounded-xl">
            <img 
            :src="tweet.img" 
            alt="img"
            class="mt-2 object-fill rounded-xl w-[85%] lg:w-full"
            >
        </div>
        <div v-else>
            <video class="h-[50%] rounded-xl w-[85%] lg:w-full" controls>
              <source src="../assets/video/amazon.mp4" type="video/mp4">
            </video>
        </div>
    </div>

    <div class="flex items-center justify-between mt-4 w-4/5 cursor-pointer">
      <div class="flex hover:bg-gray-300 p-2 rounded-full justify-center items-center">
          <MessageOutline fillColor="#5e5c5c" :size="18" />
          <span class="text-xs font-extrabold text-[#5e5c5c] ml-3">{{ tweet?.comment }}</span> 
      </div>
      <div class="flex hover:bg-gray-300 p-2 rounded-full justify-center items-center">
          <Sync fillColor="#5e5c5c" :size="18" />
          <span class="text-xs font-extrabold text-[#5e5c5c] ml-3">{{ tweet?.retweets }}</span> 
      </div>
      <div class="flex hover:bg-gray-300 p-2 rounded-full justify-center items-center">
          <HeartOutline fillColor="#5e5c5c" :size="18" />
          <span class="text-xs font-extrabold text-[#5e5c5c] ml-3">{{ tweet?.likes }}</span> 
      </div>
      <div class="flex hover:bg-gray-300 p-2 rounded-full justify-center items-center">
          <ChartBar fillColor="#5e5c5c" :size="18" />
          <span class="text-xs font-extrabold text-[#5e5c5c] ml-3">{{ tweet?.analytics }}</span> 
      </div>
    </div>
  </div>
</template>
