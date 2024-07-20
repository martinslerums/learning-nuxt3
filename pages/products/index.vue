<template>
  <div class="grid grid-cols-4 gap-5">
    <div v-for="product in products" :key="product.id">
      <ProductCard :product="product" />
    </div>
  </div>
</template>

<script setup lang="ts">
export type Product = {
  id: number;
  title: string;
  description: string;
  category: string;
  image: string | URL;
  rating: {
    rate: number;
    count: number;
  };
};

const { data: products } = await useFetch<Product[]>(
  "https://fakestoreapi.com/products"
);

useHead({
  title: "Nuxt 3 | Merch",
  meta: [
    {
      name: "description",
      content: "Nuxt 3 Merch",
    },
  ],
});
</script>

<style scoped></style>
