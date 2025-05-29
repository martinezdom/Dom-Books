# 📚 Dom Books

Dom Books es una aplicación web para la gestión y compra de libros, desarrollada con **Vue 3**, **Pinia** y **TailwindCSS**. Permite añadir, editar y eliminar, así como gestionar un carrito de compra. El backend simulado utiliza **json-server** para facilitar el desarrollo y las pruebas.

---

## 🚀 Características

- Listado de libros con información detallada.
- Añadir, editar y eliminar libros.
- Carrito de compra para gestionar adquisiciones.
- Validación de formularios con VeeValidate y Yup.
- Mensajes de éxito y error con animaciones.
- Diseño responsive con TailwindCSS.
- Backend simulado con json-server (datos en local).

---

## 🖥️ Tecnologías utilizadas

- [Vue 3](https://vuejs.org/)
- [Pinia](https://pinia.vuejs.org/)
- [TailwindCSS](https://tailwindcss.com/)
- [VeeValidate](https://vee-validate.logaretm.com/)
- [Yup](https://github.com/jquense/yup)
- [json-server](https://github.com/typicode/json-server)

---

## ⚙️ Instalación y puesta en marcha

### 1. Clona el repositorio

```sh
git clone https://github.com/martinezdom/Dom-Books.git
cd Dom-Books
```

### 2. Instala las dependencias

```sh
npm install
```

### 3. Arranca el backend simulado (json-server)

Asegúrate de tener [json-server](https://github.com/typicode/json-server) instalado globalmente o usa `npx`:

```sh
npx json-server datos.json
```

Esto levantará una API REST en `http://localhost:3000` usando el archivo `datos.json` como base de datos.

### 4. Arranca la aplicación Vue

En otra terminal, ejecuta:

```sh
npm run dev
```

La aplicación estará disponible en `http://localhost:5173` (o el puerto que indique Vite).

---

## 📝 Uso

- **Ver libros:** Página principal con todos los libros disponibles.
- **Añadir libro:** Desde el menú, opción "Añadir libro".
- **Editar libro:** Botón de editar en cada libro.
- **Eliminar libro:** Botón de eliminar en cada libro.
- **Carrito:** Añade libros al carrito y gestiona la compra.
- **Mensajes:** Recibe mensajes de éxito o error en cada acción.

---

## 🛠️ Personalización

- Puedes modificar los datos iniciales en `datos.json`.
- Variables globales o reglas específicas están en `src/assets/styles.css`.
- Las rutas y vistas están en `src/router/index.js` y `src/views/`.
- Los componentes están en `src/components/`.

---

## 🤝 Autor

Desarrollado por [Miguel Ángel Martínez](https://github.com/martinezdom)  

---

## 📄 Licencia

Este proyecto está bajo la licencia MIT.