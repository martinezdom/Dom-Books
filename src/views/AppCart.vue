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
    <h1 v-if="totalDeLibrosEnCarrito" class="text-center text-2xl font-bold mb-4">
        Total de libros en el carrito: {{ totalDeLibrosEnCarrito }}
    </h1>
    <h1 v-else class="text-center text-2xl font-bold">No hay libros en el carrito</h1>

    <div v-if="booksOnCart.length > 0"
        :class="['grid gap-x-24 gap-y-12 mx-auto my-9', booksOnCart.length >= 3 ? 'grid-cols-1 sm:grid-cols-2 lg:grid-cols-3' : booksOnCart.length === 2 ? 'grid-cols-1 sm:grid-cols-2' : 'grid-cols-1']">
        <book-item v-for="book in booksOnCart" :key="book.id" :book="book">
            <button class="button" @click="deleteBookFromCart(book.id)">
                <i class="bi bi-cart-dash"></i>
            </button>
        </book-item>
    </div>

    <div class="flex justify-center items-center gap-4 bg-white rounded-lg p-4 shadow-md max-w-xl mx-auto"
        v-if="booksOnCart.length > 0">
        <button class="button" @click="deleteAllBooksFromCart()">
            Vaciar carrito <i class="bi bi-x-circle"></i>
        </button>
        <button class="button" @click="makePurchase()">
            Realizar compra <i class="bi bi-check-circle"></i>
        </button>
    </div>
</template>
