<template>
    <img class="imge" :src="product.image" alt="">
    <p>{{ product.title }}</p>
    <NuxtLink :to="`/products/${product.id}`">view</NuxtLink>
</template>

<script setup>
    const {product} = defineProps(['product']);
</script>

<style scoped>
    .imge{
        width: 50px;
    }
</style>