<template>
  <div class="home">
    <Navbar />
    <div class="container">
      <Hero />

      <div class="row mt-4">
        <div class="col">
          <h2>Best <strong>Foods</strong></h2>
        </div>
        <div class="col">
          <router-link class="btn btn-success float-right" to="/foods">
            <b-icon-eye></b-icon-eye>Lihat Semua
          </router-link>
        </div>
      </div>

      <div class="row mb-3">
        <div class="col-md-4 mt-4">
          <CardProducts />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import Navbar from "@/components/Navbar.vue";
import Hero from "@/components/Hero.vue";
import CardProducts from "@/components/CardProducts.vue";
import axios from "axios";

export default {
  name: "Home",
  components: {
    Navbar,
    Hero,
    CardProducts,
  },
  data() {
    return {
      products: [],
    };
  },
  methods: {
    setProducts(data) {
      this.products = data;
    },
  },
  mounted() {
    axios
      .get("http://localhost:3000/best-products")
      .then((response) => console.log('berhasil', response))
      .catch((error) => console.log(error));
  },
};
</script>
