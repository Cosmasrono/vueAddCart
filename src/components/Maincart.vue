<template>
  <main>
  
    <h1
      class="flex justify-center items-center px-1 py-2 pb-2 mx-auto text-xl text-white uppercase"
    >
      Items({{ cartStore.length }})
    </h1>
    <div
      class="flex overflow-x-auto flex-row gap-3 justify-center items-center p-1 mx-auto max-w-lg text-white rounded md:max-w-4xl md:flex-nowrap"
      v-if="cartStore.length != 0"
    >
      <div
        v-for="product in cartStore"
        :key="product"
        class="flex flex-col gap-y-2 p-3 rounded border border-gray-800 bg-slate-800 md:max-w-sm"
      >
        <span
          ><img
            src="../assets/imgs/fb.jpg"
            class="object-cover w-full h-10 rounded md:h-16"
        /></span>
        <h3 class="flex justify-center items-center mx-auto text-white">
          {{ product.name }}
        </h3>

        <div class="flex justify-center items-center mx-auto text-white">
          Ksh.{{ product.cost }}
        </div>
        <button
          v-on:click="removeItemFromCart(product.id)"
          class="flex justify-center items-center px-20 py-3 mx-auto text-white rounded md:px-5 md:py-2 hover:bg-white hover:text-black bg-slate-900"
        >
          remove
        </button>
      </div>
    </div>
    <div
      class="flex justify-center items-center py-3 mx-auto text-white"
      v-else
    >
      Your cart is currently empty!! Add some products!
    </div>
   <div class="flex flex-col justify-center items-center text-3xl text-white">Total: {{ getTotal }}</div>
  <a href="https://www.paypal-mobilemoney.com/m-pesa/topup">
    <button class="flex p-5 text-white rounded-md bg-slate-900 md:mr-40">check Out</button></a>
  </main>
</template>

<script>
import { computed } from '@vue/runtime-core';
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: "Maincart",
  props: ["cartStore"],
  data() {
    return {
      items: "",
    };
  },
  methods: {
    removeItemFromCart(product) {
      // eslint-disable-next-line vue/no-mutating-props
      this.cartStore.splice(this.cartStore.indexOf(product.id));
    },
    
  },
  computed:  {getTotal() {
      return this.cartStore.reduce((a, b) => a + b.cost, 0);
}}
};
</script>
 
