<template>
    <div class="w-full max-w-[550px] max-h-[500px] flex flex-col overflow-auto gap-3">
        <div v-if="isLoading" class="text-center text-lg mt-5 font-light">
            Loading...
        </div>
        <TaskItem 
            v-else 
            v-for="(task, index) in tasks" 
            :key="task.id" 
            :id="task.id" 
            :title="task.title" 
            :is_completed="task.is_completed" 
            @completed="handleMarkAsCompleted" 
        />
    </div>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue'
import TaskItem from './TaskItem.vue'

const isLoading = ref(true)
const tasks = ref([])

const handleMarkAsCompleted = async (id: number) => {
    try {
        const response = await fetch(`http://127.0.0.1:8000/api/tasks/${id}/`, {
            method: 'PUT',
            headers: {
                'Content-Type': 'application/json',
            },
            body: JSON.stringify({
                is_completed: true,
            }),
        })

        if (response.ok) {
            // const taskIndex = tasks.value.findIndex(task => task.id === id)
            // if (taskIndex !== -1) {
            //     tasks.value[taskIndex].is_completed = true
            // }
            tasks.value = []
            isLoading.value = true
            fetchTasks()
        }
    } catch (error) {
        console.error('Failed to mark task as completed:', error)
    }
}

const fetchTasks = async () => {
 try {
        const response = await fetch('http://127.0.0.1:8000/api/tasks')
        const data = await response.json()
        tasks.value = data
        isLoading.value = false
    } catch (error) {
        console.error('Failed to fetch tasks:', error)
    }
}

onMounted(async () => {
   fetchTasks()
})
</script>

<style scoped></style>
