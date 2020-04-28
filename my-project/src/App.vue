<template>
  <div id="app">
    <h1 class="text-3xl text-gray-700 font-bold">Proyecto en vue</h1>
    <br />
    <br />
    <label>Total de elementos: {{total_unidad}}</label>
    <br />
    <label>Total: {{total_precio}}</label>
    <br />
    <br />
    <input v-model="name" />
    <input v-model="price" />
    <br />
    <br />
    <button @click="agregar">Agregar</button>
  </div>
</template>

<script>
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
      console.log(this.cart);
    }
  },
  computed: {
    total_unidad() {
      return this.cart.length;
    },
    total_precio() {
      let total = 0;
      for (const item of this.cart) {
        total += parseFloat(item.price);
      }
      return total;
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
