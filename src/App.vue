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
  <app-menu></app-menu>
  <main class="flex-1 max-w-4/5 mx-auto">
    <app-messages></app-messages>
    <router-view></router-view>
  </main>
  <footer class="flex justify-center items-center p-4 bg-secondary/60 rounded-t-2xl border-t-2 text-center mt-8"><a href="https://github.com/martinezdom" target="_blank" class="underline font-bold hover:text-secondary hover:bg-white transition-colors">Miguel Ángel Martínez<br>@martinezdom</a></footer>
</template>
