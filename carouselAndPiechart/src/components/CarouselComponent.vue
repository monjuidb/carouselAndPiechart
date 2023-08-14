<script setup>
import { ref } from "vue"
const currentIndex=ref(0)
const images =
  [
  {
    thumb: "https://images.unsplash.com/photo-1682685797769-481b48222adf?ixlib=rb-4.0.3&ixid=M3wxMjA3fDF8MHxlZGl0b3JpYWwtZmVlZHwxfHx8ZW58MHx8fHx8&auto=format&fit=crop&w=300&q=60",
    full: "https://images.unsplash.com/photo-1682685797769-481b48222adf?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDE2fHx8ZW58MHx8fHx8&auto=format&fit=crop&w=1024&q=60"
  },
  {
    thumb: "https://images.unsplash.com/photo-1682695794816-7b9da18ed470?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDZ8fHxlbnwwfHx8fHw%3D&auto=format&fit=crop&w=300&q=60",
    full: "https://images.unsplash.com/photo-1682695794816-7b9da18ed470?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDE2fHx8ZW58MHx8fHx8&auto=format&fit=crop&w=1024&q=60"
  },
  {
    thumb: "https://images.unsplash.com/photo-1682685797661-9e0c87f59c60?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDE4fHx8ZW58MHx8fHx8&auto=format&fit=crop&w=300&q=60",
    full: "https://images.unsplash.com/photo-1682685797661-9e0c87f59c60?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDE2fHx8ZW58MHx8fHx8&auto=format&fit=crop&w=1024&q=60"
  },
  {
    thumb: "https://plus.unsplash.com/premium_photo-1666963323736-5ee1c16ef19d?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDE2fHx8ZW58MHx8fHx8&auto=format&fit=crop&w=300&q=60",
    full: "https://plus.unsplash.com/premium_photo-1666963323736-5ee1c16ef19d?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDE2fHx8ZW58MHx8fHx8&auto=format&fit=crop&w=1024&q=60"
  }
]

 const previousImage=()=> {
        if (currentIndex.value > 0) {
          currentIndex.value = currentIndex.value - 1          
        }
      }
const nextImage=()=> {
        if (currentIndex.value < images.length-1) {
          currentIndex.value = currentIndex.value + 1         
        }
      }

</script>

<template>
  <main class="mx-auto w-[400px] h-[400px]  bg-white-900">
    <div x-data="imageSlider" class="relative mx-auto max-w-2xl overflow-hidden rounded-md bg-gray-100 p-2 sm:p-4">
        <div class="absolute right-5 top-5 z-10 rounded-full bg-gray-600 px-2 text-center text-sm text-white">
            <span x-text="currentIndex"></span>{{currentIndex+1}}/{{images.length}}<span x-text="images.length"></span>
        </div>

        <button @click.prevent="currentIndex=currentIndex> 0?currentIndex- 1:currentIndex" class="absolute left-5 top-1/2 z-10 flex h-11 w-11 -translate-y-1/2 items-center justify-center rounded-full bg-gray-100 shadow-md">
            <i class="fas fa-chevron-left text-2xl font-bold text-gray-500"></i>
            Pre
        </button>

        <button @click.prevent="currentIndex=currentIndex<images.length-1?currentIndex+1:currentIndex" class="absolute right-5 top-1/2 z-10 flex h-11 w-11 -translate-y-1/2 items-center justify-center rounded-full bg-gray-100 shadow-md">
            <i class="fas fa-chevron-right text-2xl font-bold text-gray-500"></i>
            Nxt
        </button>

        <div class="relative h-80" style="width: 40rem">
            <template v-for="(image,index) in images" :src="image.full" :key="image.full">
                <div :x-show="currentIndex == index + 1"  x-transition:enter="transition transform duration-300" x-transition:enter-start="opacity-0" x-transition:enter-end="opacity-100" x-transition:leave="transition transform duration-300" x-transition:leave-start="opacity-100" x-transition:leave-end="opacity-0" class="absolute top-0">
                    <img :src="images[currentIndex].full" alt=" " class="rounded-sm" />
                </div>
            </template>
        </div>
         
        
    </div>
</main>
</template>

<style scoped>

</style>

