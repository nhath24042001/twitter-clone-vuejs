<script lang="ts">
import { defineComponent } from 'vue';
import HelloWorld from '@/components/HelloWorld.vue';
import TwitterLayout from '@/components/TwitterLayout.vue';

export default defineComponent({
  name: 'HomeView',
  components: {
    HelloWorld,
    TwitterLayout
  },
});
</script>

<template>
  <div class="home">
    <HelloWorld msg="Welcome to Your Vue.js + TypeScript App"/>
    <TwitterLayout>
      <!-- <h1>Welcome</h1> -->
    </TwitterLayout>
  </div>
</template>
