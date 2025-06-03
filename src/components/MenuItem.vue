<script>
export default {
    props: {
        to: String,
        label: String
    },
}
</script>

<template>
    <li class="hover:text-primary transition-colors"><router-link :to="to">{{ label }}</router-link></li>
</template>