<script>
import { useDataStore } from '../stores/store'
import { mapState, mapActions } from 'pinia'
import { Form, Field, ErrorMessage } from "vee-validate"
import * as yup from 'yup'
export default {
  components: {
    Form,
    Field,
    ErrorMessage
  },
  props: {
    id: String
  },
  computed: {
    ...mapState(useDataStore, ['modules']),
  },
  data() {
    const mySchema = yup.object({
      moduleCode: yup.string('El módulo debe ser una cadena de texto').required('El módulo es obligatorio'),
      publisher: yup.string('La editorial debe ser una cadena de texto').required('La editorial es obligatoria'),
      price: yup.number('El precio debe ser numérico').min(0, 'El precio debe ser mayor o igual a 0').required('El precio es obligatorio'),
      pages: yup.number('El número de páginas debe ser numérico').min(0, 'El número de páginas debe ser mayor o igual a 0').integer('El número de páginas tiene que ser un número entero').required('El número de páginas es obligatorio'),
      status: yup.string('El estado debe ser una cadena de texto').required('El estado es obligatorio')
    })
    return {
      book: {},
      mySchema
    }
  },
  watch: {
    id(newValue) {
      if (!newValue) {
        this.book = {}
      } else {
        this.cargarLibro()
      }
    },
  },
  methods: {
    ...mapActions(useDataStore, ['addBook', 'editBook', 'getBook']),
    submitBook() {
      if (!this.id) {
        this.addBook(this.book)
      } else {
        this.editBook(this.book)
      }
      this.redirectList()
    },
    redirectList() {
      this.$router.push('/')
    },
    async cargarLibro() {
      if (this.id) {
        this.book = await this.getBook(this.id)
      }
    }
  },
  mounted() {
    this.cargarLibro()
  },
}
</script>

<template>
  <div id="form" class="w-full max-w-3xl mx-auto bg-white text-primary py-6 px-12 rounded-lg">
    <h3 v-if="!this.id" class="text-center text-2xl font-bold mb-3">Añadir libro</h3>
    <h3 v-else class="text-center text-2xl font-bold mb-3 ">Editando libro con ID: {{ this.id }}</h3>
    <Form id="bookForm" method="post" @submit="submitBook" :validation-schema="mySchema">
      <div id="divIdLibro" class="hidden">
        Id:
        <Field type="text" name="idBook" readonly />
      </div>
      <div class="flex flex-col gap-4">
        <div>
          <label for="moduleCode">Módulo</label>
          <Field as="select" name="moduleCode" v-model="book.moduleCode" class="form-field">
            <option value="">- Selecciona un módulo -</option>
            <option v-for="module in modules" :key="module.code" :value="module.code">{{ module.cliteral }}</option>
          </Field>
          <ErrorMessage name="moduleCode" class="block text-red-500" />
        </div>

        <div>
          <label for="publisher">Editorial</label>
          <Field type="text" name="publisher" v-model="book.publisher" class="form-field" />
          <ErrorMessage name="publisher" class="block text-red-500" />
        </div>

        <div>
          <label for="price">Precio</label>
          <Field type="number" name="price" step="0.01" v-model="book.price" class="form-field" />
          <ErrorMessage name="price" class="block text-red-500" />
        </div>

        <div>
          <label for="pages">Páginas</label>
          <Field type="number" name="pages" step="1" v-model="book.pages" class="form-field" />
          <ErrorMessage name="pages" class="block text-red-500" />
        </div>

        <div>
          <label>Estado</label>
          <div class="flex gap-4">
            <Field type="radio" name="status" value="bueno" v-model="book.status" />Bueno
            <Field type="radio" name="status" value="nuevo" v-model="book.status" />Nuevo
            <Field type="radio" name="status" value="malo" v-model="book.status" />Malo
          </div>
          <ErrorMessage name="status" class="block text-red-500" />
        </div>

        <div>
          <label for="comments">Comentarios</label>
          <Field as="textarea" name="comments" v-model="book.comments" class="form-field" />
        </div>
        <div class="flex gap-4">
          <button class="button" type="submit" v-if="!this.id">Añadir</button>
          <button class="button" type="submit" v-else>Editar</button>
          <button class="button" type="reset" v-if="!this.id">Reset</button>
          <button class="button" type="button" v-else @click="cargarLibro">Reset datos</button>
        </div>
      </div>
    </Form>
  </div>
</template>