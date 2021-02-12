<template>
  <div class="card shadow card-product">
    <img class="card-img-top" :src="productWithImage.pic" />
    <div class="card-body">
      <h5 class="cart-title">{{ product.nama }}</h5>
      <p class="card-text">Harga Rp. {{ product.harga }}</p>
      <router-link class="btn btn-success" :to="'/foods/'+product.id"><b-icon-cart></b-icon-cart> Pesan</router-link>
    </div>
  </div>
</template>

<script>
export default {
  name: "CardProduct",
  props: ["product"],
  computed: {
    productWithImage() {
      return {
        ...this.product,
        pic: this.product.gambar && require(`../assets/images/${this.product.gambar}`)
      }
    }
  }
}
</script>
