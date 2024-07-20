<template>
  <div>
    <Head>
      <Title>Nuxt 3 | {{ product?.title }}</Title>
      <Meta name="description" :content="product?.description" />
    </Head>
    <ProductDetails :product="product" />
  </div>
</template>

<script setup lang="ts">
import type { Product } from "../index.vue";

const { id } = useRoute().params;
const uri = `https://fakestoreapi.com/products/${id}`;

const { data: product } = await useFetch<Product>(uri);

if (!product.value) {
  throw createError({
    statusCode: 404,
    statusMessage: "Product not found",
    fatal: true,
  });
}

definePageMeta({
  layout: "products",
});
</script>

<style scoped></style>
