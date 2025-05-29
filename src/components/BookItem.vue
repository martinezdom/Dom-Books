<script>
import { useDataStore } from '../stores/store'
import { mapState } from 'pinia'
export default {
    props: {
        book: {
        type: Object,
        required: true
        }
    },
    computed: {
      ...mapState(useDataStore, ['cliteralFromCode'])
    },
}
</script>

<template>
  <div id="card" class="w-full max-w-xs bg-white text-primary border-2 border-secondary rounded-4xl p-6 flex flex-col items-center gap-2 mx-auto">
        <h5>Libro {{book.id}}</h5>
        <h5>{{cliteralFromCode(book.moduleCode).cliteral || '' }}</h5>
        <h5>{{book.publisher}}</h5>
        <h5>{{book.pages}} páginas</h5>
        <h5>Estado: {{book.status}}</h5>
        <h5>{{book.soldDate || "En venta"}}</h5>
        <h5>{{book.comments}}</h5>
        <h5 class="font-bold">{{book.price}}€</h5>
        <div class="flex gap-4">
          <slot></slot>
        </div>
  </div>
</template>
