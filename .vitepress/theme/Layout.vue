<template>
  <div class="antialiased">
    <div class="max-w-3xl mx-auto px-4 sm:px-6 xl:max-w-5xl xl:px-0">
      <nav class="flex justify-between items-center py-10 font-bold">
        <a class="text-xl" href="/" aria-label="The Vue Point">
          <img class="inline-block mr-2" style="width:36px" alt="logo" src="/logo.svg" />
          <span v-if="!isIndex" class="hidden md:inline">Yangming's Blog</span>
        </a>
        <div class="text-base text-gray-500 leading-5">
          <!-- <a class="hover:text-gray-700 mr-4" href="/feed.rss">RSS Feed</a> -->
          <!-- <a
            class="hover:text-gray-700"
            href="https://v3.vuejs.org"
            target="_blank"
            rel="noopener"
          >Vuejs.org →</a> -->
        </div>
      </nav>
    </div>
    <main class="max-w-3xl mx-auto px-4 sm:px-6 xl:max-w-5xl xl:px-0">
      <Home v-if="isIndex" />
      <Article v-else />
    </main>
  </div>
</template>

<script setup>
import { computed } from 'vue'
import { useRoute } from 'vitepress'
import Home from './Home.vue'
import Article from './Article.vue'

const route = useRoute()
const isIndex = computed(() => route.path.replace(/index.html$/, '') === '/')
</script>