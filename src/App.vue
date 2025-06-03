<script>
import logoDomBooks from "/logoDomBooks.png"
import AppMenu from "./components/AppMenu.vue"
import AppMessages from "./components/AppMessages.vue"
import AboutView from "./views/AboutView.vue"
import { useDataStore } from './stores/store'
import { mapActions } from 'pinia'
export default {
  components: {
    AppMenu,
    AppMessages,
    AboutView,
  },
  data() {
    return {
      logoDomBooks: logoDomBooks,
    }
  },
  methods: {
    ...mapActions(useDataStore, ['populateBooks', 'populateModules']),
  },
  mounted() {
    this.populateBooks()
    this.populateModules()
  }
}
</script>

<template>
  <app-menu />
  <main class="flex-1 max-w-4/5 mx-auto animate-blurred-fade-in animate-duration-500">
    <app-messages />
    <router-view />
  </main>
  <footer class="flex justify-center items-center flex-col p-4 bg-secondary/60 rounded-t-2xl border-t-2 text-center mt-8"><a href="https://github.com/martinezdom" target="_blank" class="font-bold hover:text-secondary hover:bg-text transition-colors animate-fade-in">Miguel Ángel Martínez</a><a href="https://github.com/martinezdom" target="_blank" class="font-bold hover:text-secondary hover:bg-text transition-colors animate-fade-in animate-delay-200">@martinezdom</a></footer>
</template>
