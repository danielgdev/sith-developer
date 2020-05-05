<template>
  <div id="app" class="w-full min-h-screen flex">
    <div class="w-1/2 min-h-screen p-4">
      <h1 class="text-3xl text-gray-700 font-bold mb-8">Carro de compras en Vue</h1>
      <input v-model="name" placeholder="Nombre del producto" />
      <input v-model="price" />
      <span v-if="'' != name && price > 0" class="inline-flex rounded-md shadow-sm mt-6">
        <button
          class="inline-flex items-center px-4 py-2 border border-gray-300 text-sm leading-5 font-medium rounded-md text-gray-700 bg-white hover:text-gray-500 focus:outline-none focus:border-blue-300 focus:shadow-outline-blue active:text-gray-800 active:bg-gray-50 transition ease-in-out duration-150"
          @click="agregar"
        >Agregar</button>
      </span>
      <span v-else>
        <p class="text-xs mt-4 text-red-300">Escribe el nombre de producto y un precio.</p>
      </span>
    </div>
    <detalle :cart="cart" />
  </div>
</template>

<script>
import Detalle from "./components/Detalle";

export default {
  name: "App",
  data() {
    return {
      cart: [],
      name: "",
      price: 0
    };
  },
  methods: {
    agregar() {
      this.cart.push({
        name: this.name,
        price: this.price
      });
      this.name = "";
      this.price = 0;
    }
  },
  components: {
    Detalle
  }
};
</script>

<style>
html,
body {
  color: #4e4e4e;
  font-size: 16px;
  height: 100%;
  margin: 0;
  padding: 0;
  width: 100%;
}
body {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  font-size: 16px;
}
*,
:after,
:before {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
</style>
