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
    <div id="list" class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-8 mx-auto">
        <book-item v-for="book in books" :key="book.id" :book="book">
            <button class="addCart button" @click="addBookToCart(book)" v-if="!bookOnCart(book.id)">
                <span><i class="bi bi-cart-plus"></i></span>
            </button>
            <button class="editBook button" @click="editarLibro(book)">
                <span><i class="bi bi-pencil"></i></span>
            </button>
            <button class="remove button" @click="deleteBook(book.id)">
                <span><i class="bi bi-trash"></i></span>
            </button>
        </book-item>
    </div>
</template>