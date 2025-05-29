<script>
import { useDataStore } from '../stores/store'
import { mapState, mapActions } from 'pinia'
import BookItem from "../components/BookItem.vue"
    export default {
        components: {
            BookItem
        },
        computed: {
            ...mapState(useDataStore, ['booksOnCart', 'totalDeLibrosEnCarrito']),
        },
        methods: {
            ...mapActions(useDataStore, ['deleteBookFromCart', 'deleteAllBooksFromCart', 'makePurchase']),
        }
    }
</script>

<template>
    <h1 class="text-center text-2xl font-bold mb-4">Total de libros en el carrito: {{ totalDeLibrosEnCarrito }}</h1>
    <div id="list">
        <book-item v-for="book in booksOnCart" :key="book.id" :book="book">
            <button class="button" type="button" @click="deleteBookFromCart(book.id)"><span><i class="bi bi-cart-dash"></i></span></button>
        </book-item>
    </div>
        <button class="button" type="button" @click="makePurchase"><span><i class="bi bi-check-circle"></i></span></button>
        <button class="button" type="button" @click="deleteAllBooksFromCart"><span><i class="bi bi-x-circle"></i></span></button>
</template>