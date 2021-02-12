<template>
  <div class="card shadow card-product">
    <img class="card-img-top" :src="getImgUrl(product.gambar)" />
    <div class="card-body">
      <h5 class="cart-title">{{ product.nama }}</h5>
      <p class="card-text">Harga Rp. {{ product.harga }}</p>
      <a href="#" class="btn btn-success"><b-icon-cart></b-icon-cart> Pesan</a>
    </div>
  </div>
</template>

<script>
export default {
  name: "CardProduct",
  props: ["product"],
  methods: {
    getImgUrl(pic) {
      return require("../assets/images/" + pic);
    },
  },
};
</script>

<style></style>
