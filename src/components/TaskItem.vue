<template>
    <div class="border h-[150px] flex items-center gap-3 justify-between py-3 px-4">
        <h2 class="text-lg font-bold break-words max-w-[60%]">{{ title }}</h2>
        <button 
            v-if="!is_completed" 
            type="button"
            class="bg-blue-500 border rounded text-white p-3 transition-colors duration-100 ease-in-out hover:bg-blue-400 hover:shadow-md" 
            @click="emit('completed', id)"
        >
            Mark as Completed
        </button>
        <button 
            v-else 
            type="button"
            class="bg-green-500 border rounded text-white p-3" 
            disabled
        >
        Completed
        </button>
    </div>

</template>

<script setup lang="ts">
const props = defineProps({
    id: {
        type: Number || String,
        required: true
    },
    title: {
        type: String,
        required: true
    },
    is_completed: {
        type: Boolean,
        required: false,
        default: false
    }
})

const emit = defineEmits(['completed'])
</script>

<style scoped>

</style>