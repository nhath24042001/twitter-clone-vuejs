<script lang="ts">
import { defineComponent } from 'vue';
import HelloWorld from '@/components/HelloWorld.vue';
import TwitterLayout from '@/components/TwitterLayout.vue';
import TweetItem from '@/components/TweetItem.vue';

export default defineComponent({
  name: 'HomeView',
  components: {
    HelloWorld,
    TwitterLayout,
    TweetItem
  },
});
</script>

<template>
  <div class="home">
    <HelloWorld msg="Welcome to Your Vue.js + TypeScript App"/>
    <TwitterLayout>
      <div class="text-white">
        <div class="flex ">
          <TweetItem :tweet="{
          name: 'Huy',
          handle: '@nhath240401',
          img: 'https://images.unsplash.com/photo-1670272498425-e13ce4fcf5f0?ixlib=rb-4.0.3&ixid=MnwxMjA3fDF8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=870&q=80',
          tweet: 'We went rock climbing this weekend? Here is the video. Climbing is way more fun',
          is_Video: true,
          comment: '35',
          retweets: '54',
          likes: '88',
          analytics: '81'
        }" />
        </div>
        <div class="border-b border-b-gray-800 mt-2">
      
        </div>
      </div>
      <!-- <h1>Welcome</h1> -->
    </TwitterLayout>
  </div>
</template>
