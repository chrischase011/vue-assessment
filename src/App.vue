<script setup lang="ts">
import TaskContainer from './components/TaskContainer.vue'
import NotificationBanner from './components/NotificationBanner.vue'
</script>

<template>
  <div class="container mx-auto flex flex-col items-center justify-center h-screen my-7 gap-5">
    <h1 class="text-4xl font-bold">Vue 3</h1>
    <NotificationBanner message="Hello world! This is a Notification Banner" />
    <TaskContainer /> 
  </div>

</template>

<style scoped>

</style>
