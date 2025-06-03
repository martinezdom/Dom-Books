<script>
import { useDataStore } from '../stores/store'
import { mapState, mapActions } from 'pinia'
import BookItem from "../components/BookItem.vue"
export default {
    components: {
        BookItem
    },
    computed: {
        ...mapState(useDataStore, ['books', 'totalDeLibros', 'bookOnCart']),
    },
    methods: {
        ...mapActions(useDataStore, ['deleteBook', 'addBookToCart']),
        editarLibro(book) {
            this.$router.push({ name: 'edit', params: { id: book.id } })
        }
    }
}
</script>

<template>
    <h1 v-if="totalDeLibros" class="text-center text-2xl font-bold mb-4">
        Total de libros: {{ totalDeLibros }}
    </h1>
    <h1 v-else class="text-center text-2xl font-bold mb-4">
        No hay libros disponibles
    </h1>

    <div v-if="books.length > 0" :class="['grid gap-x-24 gap-y-12 mx-auto', books.length >= 3 ? 'grid-cols-1 sm:grid-cols-2 lg:grid-cols-3' : books.length === 2 ? 'grid-cols-1 sm:grid-cols-2' : 'grid-cols-1']">
        <book-item v-for="book in books" :key="book.id" :book="book">
            <button class="addCart button animate-fade-in-up" @click="addBookToCart(book)" v-if="!bookOnCart(book.id)">
                <i class="bi bi-cart-plus"></i>
            </button>
            <button class="editBook button animate-fade-in-up animate-delay-100" @click="editarLibro(book)">
                <i class="bi bi-pencil"></i>
            </button>
            <button class="remove button animate-fade-in-up animate-delay-200" @click="deleteBook(book.id)">
                <i class="bi bi-trash"></i>
            </button>
        </book-item>
    </div>
</template>
