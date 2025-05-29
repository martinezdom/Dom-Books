<script>
import logoDomBooks from '/logoDomBooks.png'
import MenuItem from './MenuItem.vue';
export default {
  components: {
    MenuItem,
  },
  data() {
    return {
      logoDomBooks,
      menuItems: [
        { to: '/', label: 'Ver libros' },
        { to: '/addBook', label: 'Añadir libro' },
        { to: '/cart', label: 'Ver carrito' },
        { to: '/about', label: 'Acerca de...' },
      ]
    }
  }
}
</script>

<template>
  <header class="bg-secondary/60 rounded-b-2xl border-b-2 mb-8">
    <nav class="flex flex-col p-4 gap-2 lg:flex-row lg:justify-between lg:px-20">
      <div class="flex items-center justify-center w-15 mx-auto lg:mx-0">
        <router-link to="/">
          <img alt="Logo web" class="logo size-10 hover:scale-110 transition-transform" :src="logoDomBooks" />
        </router-link>
      </div>
      <div class="flex justify-center items-center">
        <ul class="flex gap-10 text-mobile lg:text-desktop transition-all duration-300">
          <menu-item v-for="item in menuItems" :key="item.to" :to="item.to" :label="item.label"></menu-item>
        </ul>
      </div>
    </nav>
  </header>
</template>
