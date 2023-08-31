<template>
    <div class="card text-center">
        <img :src="plays_l.preview" alt="product thumb" class="thumb">
        <p class="font-bold text-gray-500 m-4 truncate">{{ plays_l.video_title }}</p>

    </div>
</template>

<script setup lang="ts">
    const { plays_l } = defineProps(['plays_l'])
</script>

<style scoped>
    .thumb {
        max-height: 150px;
        max-width: 70%;
        margin: 0 auto;
    }
</style>