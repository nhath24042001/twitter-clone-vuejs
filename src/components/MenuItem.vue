<script lang="ts">
import { defineComponent } from "vue";
import Home from "vue-material-design-icons/Home.vue";
import Pound from "vue-material-design-icons/Pound.vue";
import BellOutline from "vue-material-design-icons/BellOutline.vue";
import EmailOutline from "vue-material-design-icons/EmailOutline.vue";
import AccountOutline from "vue-material-design-icons/AccountOutline.vue";

export default defineComponent({
  components: {
    Home,
    Pound,
    BellOutline,
    EmailOutline,
    AccountOutline,
  },
});
</script>

<template>
  <div class="">
    <RouterLink to="/">
    <div
      class="w-full lg:inline-block flex justify-center items-center hover:bg-gray-900 p-4 lg-pr-6 rounded-full cursor-pointer transition duration-300 ease-in-out mt-5"
    >

      <div class="flex items-center">
        <Home fillColor="#FFFFFF" :size="32" />
        <span
        class="lg:block hidden text-white font-extrabold text-[18px] pl-4 mt-0.5"
        >
        Home
      </span>
    </div>
  </div>
</RouterLink>

    <RouterLink to='/explore'>

      <div
      class="w-full lg:inline-block flex justify-center items-center hover:bg-gray-900 p-4 px-4 lg-pr-6 rounded-full cursor-pointer transition duration-300 ease-in-out mt-5"
      >
      <div class="flex items-center">
        <Pound fillColor="#FFFFFF" :size="32" />
        <span
        class="lg:block hidden text-white font-bold text-[18px] pl-4 mt-0.5"
        >
        Explore
      </span>
    </div>
  </div>
  </RouterLink>
  
  <div
      class="w-full lg:inline-block flex justify-center items-center hover:bg-gray-900 p-4 px-4 lg-pr-6 rounded-full cursor-pointer transition duration-300 ease-in-out mt-5"
    >
      <div class="flex items-center">
        <BellOutline fillColor="#FFFFFF" :size="32" />
        <span
          class="lg:block hidden text-white font-extrabold text-[18px] pl-4 mt-0.5"
        >
          Notification
        </span>
      </div>
    </div>
    <div
      class="w-full lg:inline-block flex justify-center items-center hover:bg-gray-900 p-4 px-4 lg-pr-6 rounded-full cursor-pointer transition duration-300 ease-in-out mt-5"
    >
      <div class="flex items-center">
        <EmailOutline fillColor="#FFFFFF" :size="32" />
        <span
          class="lg:block hidden text-white font-extrabold text-[18px] pl-4 mt-0.5"
        >
          Messages
        </span>
      </div>
    </div>
    <RouterLink to="/profile">
      <div
        class="w-full lg:inline-block flex justify-center items-center hover:bg-gray-900 p-4 px-4 lg-pr-6 rounded-full cursor-pointer transition duration-300 ease-in-out mt-5"
      >
        <div class="flex items-center">
          <AccountOutline fillColor="#FFFFFF" :size="32" />
          <span
            class="lg:block hidden text-white font-extrabold text-[18px] pl-4 mt-0.5"
          >
            Profile
          </span>
        </div>
      </div>
    </RouterLink>
  </div>
</template>
