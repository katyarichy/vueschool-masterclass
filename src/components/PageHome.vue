<template>
    <div>Hello from PageHome</div>
    <div v-for="thread in threads" :key="thread.id">
        <h2>{{ thread.title }}</h2>
        <div v-for="postId in thread.posts" :key="postId">
            <p>{{ userById(postById(postId).userId).name }}</p>
            <p>{{ postById(postId).text }}</p>
        </div>
    </div>
</template>

<style></style>

<script setup>
import sourceDate from '@/data.json'
import { ref } from 'vue'

const threads = ref(sourceDate.threads)
const posts = ref(sourceDate.posts)
const users = ref(sourceDate.users)

function postById(postId) {
    return posts.value.find(p => p.id === postId)
}

function userById(userId) {
    return users.value.find(u => u.id === userId)
}
</script>
