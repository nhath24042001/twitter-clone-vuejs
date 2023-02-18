<script lang="ts">
import { defineComponent } from "vue";
import Twitter from "vue-material-design-icons/Twitter.vue";
import Magnify from "vue-material-design-icons/Magnify.vue";
import DotsHorizontal from "vue-material-design-icons/DotsHorizontal.vue";
import Feather from "vue-material-design-icons/Feather.vue";
import Close from "vue-material-design-icons/Close.vue";
import ChevronDown from "vue-material-design-icons/ChevronDown.vue";
import Earth from "vue-material-design-icons/Earth.vue";
import ImageOutline from "vue-material-design-icons/ImageOutline.vue";
import FileGifBox from "vue-material-design-icons/FileGifBox.vue";
import Emoticon from "vue-material-design-icons/Emoticon.vue";
import ArrowLeft from "vue-material-design-icons/ArrowLeft.vue";

import MenuItem from "./MenuItem.vue";

export default defineComponent({
  data() {
    return {
      images: [
        "https://images.unsplash.com/photo-1674574124649-778f9afc0e9c?ixlib=rb-4.0.3&ixid=MnwxMjA3fDF8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=2070&q=80",
        "https://images.unsplash.com/photo-1674574124349-0928f4b2bce3?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1yZWxhdGVkfDF8fHxlbnwwfHx8fA%3D%3D&auto=format&fit=crop&w=600&q=60",
      ],
      imageItem: [
        "https://plus.unsplash.com/premium_photo-1674638478472-4ef31f335ccb?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=387&q=80",
      ],
      tweet: "",
      showUpload: '',
      uploadType: '',
      selectedImage: null,
      ranImg: null,
      textarea: null,
      createTweet: false,
      file: ''
    };
  },
  components: {
    Twitter,
    Magnify,
    Feather,
    DotsHorizontal,
    ArrowLeft,
    Close,
    ChevronDown,
    Earth,
    ImageOutline,
    FileGifBox,
    Emoticon,
    MenuItem,
  },
  methods: {
    randomItem(items: string | any) {
      return items[Math.floor(Math.random() * items.length)];
    },
    getFile() {
      console.log("");
    },
    closeMessageBox: function(){
      this.createTweet = false
      this.tweet = ''
      this.showUpload = ''
      this.uploadType = ''
    }
  },
  created() {
    (this.selectedImage = this.randomItem(this.images)),
      (this.ranImg = this.randomItem(this.imageItem));
  },
});
</script>

<template>
  <div class="fixed w-full">
    <div class="max-w-[1400px] flex mx-auto">
      <!--Sidebar-->
      <div
        class="hidden md:block lg:w-3/12 w-[60px] h-[100vh] max-w-[350px] lg:px-4 lg:mx-auto mx-5 mt-5"
      >
        <div class="p-2 px-3 mb-4">
          <Twitter fillColor="#FFFFFF" :size="37" />
        </div>

        <MenuItem />

        <button @click="createTweet = true"
          class="lg:w-[75%] mt-8 ml-2 text-white font-extrabold text-[22px] bg-[#1C9CEF] p-3 px-3 rounded-full cursor-pointer hover:bg-blue-500"
        >
          <span class="lg:block hidden">Tweet</span>
          <span class="block lg:hidden">
            <Feather />
          </span>
        </button>
      </div>

      <div
        class="lg:w-7/12 w-11/12 border-x border-gray-800 relative text-white"
      >
        <div
          class="bg-black bg-opacity-50 backdrop-blur-md z-10 absolute w-full"
        >
          <div
            class="border-gray-800 border-b w-full font-extrabold p-4 text-[21px]"
          >
            Home
          </div>
          <div class="flex">
            <div
              class="flex items-center justify-center w-full h-[60px] text-white text-[17px] font-extrabold p-4 hover:bg-gray-500 hover:bg-opacity-30 cursor-pointer transition duration-300 ease-in"
            >
              <div
                class="inline-block text-center border-b-4 border-b-[#1C9CEF] h-[60px]"
              >
                <div class="my-auto mt-4">For you</div>
              </div>
            </div>
            <div
              class="flex items-center justify-center w-full h-[60px] text-white text-[17px] font-extrabold p-4 hover:bg-gray-500 hover:opacity-30 cursor-pointer transition duration-300 ease-in"
            >
              <div class="text-center">Following</div>
            </div>
          </div>
        </div>

        <div class="absolute top-0 z-0 h-full overflow-auto scrollbar-hide">
        <div class="mt-[126px]"></div>
        <slot />
        <div class="pb-4"></div>
      </div>
      </div>

      <!---->
      <!--Trending-->
      <div
        class="lg:block hidden lg:w-4/12 h-screen border-1 border-gray-800 pl-4 mt-2"
      >
        <div
          class="w-full p-1 mt-2 px-4 lg:flex items-center rounded-full hidden bg-[#212327]"
        >
          <Magnify fillColor="#5e5c5c" :size="25" class="mr-2" />
          <input
            type="text"
            placeholder="Search Twitter"
            class="appearance-none w-full border-0 py-2 bg-[#212327] text-gray-100 placeholder-gray-500 leading-right outline-none focus:ring-0"
          />
        </div>

        <div class="w-full mt-4 rounded-lg lg:block hidden bg-[#212327]">
          <div class="w-full p-4 text-white font-extrabold mb-4 text-[22px]">
            Trending for you
          </div>

          <div
            class="h-[90px] hover:bg-gray-800 cursor-pointer transition duration-300 ease-in"
          >
            <div class="flex p-3 justify-between h-[80px] py-3">
              <div>
                <div class="text-[14px] text-gray-400">
                  Tennis Tournament LIVE
                </div>
                <div class="w-full text-white font-extrabold mb-6 text-[17px]">
                  Vietnam Open 2023
                </div>
              </div>
              <p v-if="selectedImage">
                <img
                  style="width: 100%"
                  :src="selectedImage"
                  alt="img"
                  class="rounded-xl h-[60px] object-cover"
                />
              </p>
            </div>
          </div>

          <div
            class="hover:bg-gray-800 cursor-pointer transition duration-300 ease-in"
          >
            <div class="flex p-3 justify-between">
              <div>
                <div class="text-[14px] text-gray-400">
                  Tennis Tournament LIVE
                </div>
                <div class="w-full text-white font-extrabold text-[17px]">
                  Vietnam Open 2023
                </div>
                <div class="text-[14px] text-gray-400">5.923 Tweets</div>
              </div>
              <DotsHorizontal fillColor="#5e5c5c" :size="25" />
            </div>
          </div>

          <div
            class="hover:bg-gray-800 cursor-pointer transition duration-300 ease-in"
          >
            <div class="flex p-3 justify-between">
              <div>
                <div class="text-[14px] text-gray-400">
                  Tennis Tournament LIVE
                </div>
                <div class="w-full text-white font-extrabold text-[17px]">
                  Vietnam Open 2023
                </div>
                <div class="text-[14px] text-gray-400">5.923 Tweets</div>
              </div>
              <DotsHorizontal fillColor="#5e5c5c" :size="25" />
            </div>
          </div>

          <div
            class="hover:bg-gray-800 cursor-pointer transition duration-300 ease-in"
          >
            <div class="flex p-3 justify-between">
              <div>
                <div class="text-[14px] text-gray-400">
                  Tennis Tournament LIVE
                </div>
                <div class="w-full text-white font-extrabold text-[17px]">
                  Vietnam Open 2023
                </div>
                <div class="text-[14px] text-gray-400">5.923 Tweets</div>
              </div>
              <DotsHorizontal fillColor="#5e5c5c" :size="25" />
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
  
  <!--Overplay section-->
  <div
    v-if="createTweet"
    id="OverplaySection"
    class="fixed top-0 left-0 w-full h-screen bg-black md:bg-gray-400 md:bg-opacity-30"
  >
    <div class="md:max-w-xl md:mx-auto md:mt-[150px] md:rounded-xl bg-black">
      <div
        class="flex items-center justify-between md:inline-block p-2 m-2 rounded-full cursor-pointer"
      >
        <div @click="closeMessageBox()"
          class="hover:bg-gray-800 inline-block p-2 rounded-full cursor-pointer"
        >
          <Close fillColor="#FFFFFF" :size="28" class="md:block hidden" />
          <ArrowLeft fillColor="#FFFFFF" :size="28" class="md:hidden block" />
        </div>

        <button
          :disabled="!tweet"
          :class="
            tweet ? 'bg-[#1C9CEF] text-white' : 'bg-[#124D77] text-gray-400'
          "
          class="md:hidden font-extrabold text-[15px] p-1.5 px-4 rounded-full cursor-pointer"
        >
          Tweet
        </button>
      </div>

      <div class="w-full flex">
        <div class="ml-3.5 mr-2">
          <p v-if="ranImg">
            <img
              :src="ranImg"
              alt="img"
              class="rounded-full h-[50px] w-[50px] object-cover"
            />
          </p>
        </div>
        <div class="w-[calc(100%-100px)]">
          <div class="inline-block">
            <div class="flex items-center border border-gray-700 rounded-full">
              <span class="text-[#1C9CEF] p-0.5 pl-3.5 font-extrabold"
                >Everyone</span
              >
              <ChevronDown class="pr-2" fillColor="#1C9CEF" :size="25" />
            </div>
          </div>
          <div>
            <textarea
              cols="30"
              rows="4"
              placeholder="What's happening?"
              v-model="tweet"
              ref="textarea"
              class="w-full bg-black border-0 mt-2 focus:ring-0 text-white text-[19px] font-extrabold min-h-[120px]"
            >
            </textarea>
          </div>

          <div class="flex py-2 items-center text-[#1C9CEF] font-extrabold">
            <Earth class="pr-2" fillColor="#1C9CEF" :size="20" /> Everyone can
            reply
          </div>

          <div class="border-b border-b-gray-700"></div>
          <div class="flex items-center justify-between py-2">
            <div class="flex items-center">
              <div
                class="hover:bg-gray-800 inline-block p-2 rounded-full cursor-pointer"
              >
                <label for="fileUpload" class="cursor-pointer">
                  <ImageOutline fillColor="#1C9CEF" :size="25" />
                  <input
                    type="file"
                    id="fileUpload"
                    class="hidden"
                    @change="getFile"
                  />
                </label>
              </div>
              <div
                class="hover:bg-gray-800 inline-block p-2 rounded-full cursor-pointer"
              >
                <FileGifBox fillColor="#1C9CEF" :size="25" />
              </div>
              <div
                class="hover:bg-gray-800 inline-block p-2 rounded-full cursor-pointer"
              >
                <Emoticon fillColor="#1C9CEF" :size="25" />
              </div>
            </div>

            <button
              :disabled="!tweet"
              :class="
                tweet ? 'bg-[#1C9CEF] text-white' : 'bg-[#124D77] text-gray-400'
              "
              class="hidden md:block font-extrabold text-[15px] p-1.5 px-4 rounded-full cursor-pointer"
            >
              Tweet
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style>
body {
  background-color: black;
}
</style>
