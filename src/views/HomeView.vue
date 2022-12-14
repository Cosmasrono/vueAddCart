<template>

  <main class="min-h-screen bg-slate-700">
    
    <!-- Cart -->
    <div class="py-2">
      <button
        v-on:click="showCart"
        class="flex justify-center items-center px-20 py-3 pt-1 mx-auto text-white rounded md:px-5 md:py-2 bg-slate-900"
      >
        {{ showed ? "close cart" : "view cart" }}
      </button>
    </div>
    <div v-if="showed">
      <div v-show="showed">
        <Maincart :cartStore="cartStore" />
      </div>
    </div>
    <div v-else>
      <h1
        class="flex justify-center items-center px-1 py-2 pb-2 mx-auto text-2xl text-white uppercase"
      >
        products
      </h1>

      <div
        class="grid flex-wrap grid-cols-2 grid-flow-row gap-3 justify-center items-center p-1 mx-auto max-w-lg rounded md:max-w-4xl md:grid-cols-3 lg:grid-cols-4 md:flex-nowrap"
      >
        <div
          v-for="product in products"
          :key="product"
          class="flex flex-col gap-y-2 p-3 rounded border border-gray-800 bg-slate-800 md:max-w-lg"
        >
          <span
            ><img
              src="../assets/imgs/fb.jpg"
              class="object-cover w-full h-40 rounded"
          /></span>
          <h3 class="flex justify-center items-center mx-auto text-white">
            {{ product.name }}
          </h3>

          <div class="flex justify-center items-center mx-auto text-white">
            Ksh.{{ product.cost }}
          </div>
          <button
            v-on:click="addItemToCart(product)"
            class="flex justify-center items-center px-20 py-3 mx-auto text-white rounded md:px-5 md:py-2 hover:bg-white hover:text-black bg-slate-900"
          >
            add
          </button>
        </div>
      </div>
    </div>
 <footer class="rounded-lg shadow md:px-6 md:py-8">
    <div class="sm:flex sm:items-center sm:justify-between">
    </div>
    <!-- <hr class="my-6 border-gray-200 sm:mx-auto dark:border-gray-700 lg:my-8" /> -->
    <span class="block text-sm text-white sm:text-center dark:text-gray-400">©Cossi Wing001. All Rights Reserved.
    </span>
</footer>

  </main>
  

</template>
<script>
import Maincart from "../components/Maincart.vue";
export default {
  name: "app",
  data() {
    return {
      cartStore: [],
      showed: false,
      products: [
        {
          id: 1,
          name: "cosmas1",
          cost: 2000,
        },
        {
          id: 2,
          name: "cosmas2",
          cost: 1500,
        },
        {
          id: 3,
          name: "cosmas3",
          cost: 1400
        },
        {
          id: 4,
          name: "cosmas4",
          cost: 1300,
        },
        {
          id: 5,
          name: "cosmas",
          cost: 1200,
        },
        {
          id: 6,
          name: "cosmas",
          cost: 1000,
        },
        {
          id: 7,
          name: "cosmas",
          cost: 200,
        },
        {
          id: 8,
          name: "cosmas",
          cost: 300,
        },
        {
          id: 9,
          name: "cosmas",
          cost: 500,
        },
        {
          id: 10,
          name: "cosmas",
          cost: 500,
        },
        {
          id: 11,
          name: "cosmas",
          cost: 600,
        },
        {
          id: 12,
          name: "cosmas",
          cost: 900,
        },
      ],
    };
  },
  
  methods: {
    addItemToCart(product) {
      this.cartStore.push(product);
      console.log(this.cartStore);
    },
    showCart() {
      this.showed = !this.showed;
},


  },
  components: { Maincart },
};
</script>

<style></style>
