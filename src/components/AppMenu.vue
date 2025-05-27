<script>
import { ref } from 'vue'
import logoDomBooks from '/logoDomBooks.png'
export default {
  data() {
    return {
      logoDomBooks: logoDomBooks
    }
  }
}
</script>

<template>
  <header class="bg-secondary-opacity rounded-b-2xl">
    <nav class="flex flex-col p-4 gap-2 lg:flex-row lg:justify-between lg:px-20">
      <div class="flex items-center justify-center">
        <router-link to="/">
          <img alt="Logo web" class="logo size-10 hover:scale-110 transition-transform" :src="logoDomBooks" />
        </router-link>
      </div>
      <div>
        <ul class="flex justify-center gap-10 text-mobile lg:text-desktop">
          <li class="hover:text-primary transition-colors"><router-link to="/">Ver libros</router-link></li>
          <li class="hover:text-primary transition-colors"><router-link to="/addBook">Añadir libro</router-link></li>
          <li class="hover:text-primary transition-colors"><router-link to="/cart">Ver carrito</router-link></li>
          <li class="hover:text-primary transition-colors"><router-link to="/about">Acerca de...</router-link></li>
        </ul>
      </div>
    </nav>
  </header>
</template>
