<script>
import { useDataStore } from "../stores/store";
import { mapState, mapActions } from "pinia";

export default {
    computed: {
        ...mapState(useDataStore, ["messages"]),
    },
    methods: {
        ...mapActions(useDataStore, ["deleteMessageById"]),
    },
};
</script>

<template>
    <div class="flex flex-col justify-center items-center">
        <div v-for="(message, index) in messages" :key="index" :class="['message', `message-${message.type}`]"
            id="messages">
            {{ message.text }}
            <button type="button" :class="['button--close', `button--close--${message.type}`]" @click="deleteMessageById(message.id)">
                <span><i class="bi bi-x"></i></span>
            </button>
        </div>
    </div>
</template>
