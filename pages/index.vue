<template>
  <MainLayout>
    <div id="IndexPage" class="mt-4 max-w-[1200px] mx-auto px-2">
      <div
        class="grid xl:grid-cols-6 lg:grid-cols-5 md:grid-cols-4 sm:grid-cols-3 grid-cols-2 gap-4"
      >
        <div v-if="products" v-for="product in products.data" :key="product">
          <ProductComponent :product="product" />
        </div>
      </div>
    </div>
  </MainLayout>
</template>

<script setup>
import MainLayout from "@/layouts/MainLayout.vue";
import { useUserStore } from "@/stores/user";
const userStore = useUserStore();

let products = ref(null);

onBeforeMount(async () => {
    products.value = await useFetch('/api/prisma/get-all-products')
    setTimeout(() => userStore.isLoading = false, 1000)
})

// onBeforeMount(async () => {
//   products.value = [
//     {
//       id: 1,
//       title: "Title 1",
//       description: "thisis a description for product 1",
//       url: "https://picsum.photos/id/7/800/800",
//       price: 9999,
//     },
//     {
//       id: 2,
//       title: "Title 2",
//       description: "thisis a description for product 2",
//       url: "https://picsum.photos/id/72/800/800",
//       price: 9992,
//     },
//     {
//       id: 3,
//       title: "Title 3",
//       description: "thisis a description for product 3",
//       url: "https://picsum.photos/id/73/800/800",
//       price: 9993,
//     },
//     {
//       id: 4,
//       title: "Title 4",
//       description: "thisis a description for product 4",
//       url: "https://picsum.photos/id/74/800/800",
//       price: 9994,
//     },
//     {
//       id: 5,
//       title: "Title 5",
//       description: "thisis a description for product 5",
//       url: "https://picsum.photos/id/75/800/800",
//       price: 9995,
//     },
//     {
//       id: 6,
//       title: "Title 6",
//       description: "thisis a description for product 6",
//       url: "https://picsum.photos/id/76/800/800",
//       price: 9996,
//     },
//     {
//       id: 7,
//       title: "Title 7",
//       description: "thisis a description for product 7",
//       url: "https://picsum.photos/id/77/800/800",
//       price: 9997,
//     },
//     {
//       id: 8,
//       title: "Title 8",
//       description: "thisis a description for product 8",
//       url: "https://picsum.photos/id/78/800/800",
//       price: 9998,
//     },
//     {
//       id: 9,
//       title: "Title 9",
//       description: "thisis a description for product 9",
//       url: "https://picsum.photos/id/79/800/800",
//       price: 9999,
//     },
//     {
//       id: 10,
//       title: "Title 10",
//       description: "thisis a description for product 10",
//       url: "https://picsum.photos/id/80/800/800",
//       price: 99910,
//     },
//   ];
// });
</script>
