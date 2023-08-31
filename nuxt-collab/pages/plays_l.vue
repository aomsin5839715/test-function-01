<template>
    <div>
        <div class="grid grid-cols-4 gap-5">
            <div v-for="p in plays_l">
                <PlaysCard_l :plays_l="p" />
            </div>
        </div>
    </div>
</template>

<script setup lang="ts">
   //definePageMeta({
   //     layout:'plays_l'
   // })

    // fetch data
    const { data: plays_l} = await useFetch('https://fuzik03.tetraserver.com/plays_l/')

    useHead({
    title: 'Inventory | Videos Page',
    meta: [
      { name: 'description', content: 'List Play video'}
    ]
  })
</script>

<style scoped>

</style>