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
    <app-messages></app-messages>
    <router-view></router-view>
    <footer>Miguel Ángel Martínez</footer>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/icon?family=Material+Icons')

</style>
