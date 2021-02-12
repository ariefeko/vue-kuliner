<template>
  <div class="food-detail">
    <Navbar />
    <div class="container">

      <!-- Breadcrumb -->
      <div class="row mt-5">
        <div class="col">
          <nav aria-label="breadcrumb">
            <ol class="breadcrumb">
              <li class="breadcrumb-item">
                <router-link to="/" class="text-dark">Home</router-link>
              </li>
              <li class="breadcrumb-item">
                <router-link to="/foods" class="text-dark">Foods</router-link>
              </li>
              <li class="breadcrumb-item active" aria-current="page">Food Order</li>
            </ol>
          </nav>
        </div>
      </div>

      <!-- Product Detail -->
      <div class="row">
        <div class="col-md-6">
          <img :src="productWithImage.pic" class="img-fluid shadow">
        </div>
        <div class="col-md-6">
          <h2><strong>{{ product.nama }}</strong></h2>
          <hr>
          <h4>Harga : <strong>Rp. {{ product.harga }}</strong></h4>
          <form class="mt-4">
            <div class="form-group">
              <label for="jumlah_pemesanan">Jumlah Pesan</label>
              <input type="number" class="form-control">
            </div>
            <div class="form-group">
              <label for="keterangan">Keterangan</label>
              <textarea class="form-control" placeholder="Keterangan spt: Pedes, Nasi Setengah ..."></textarea>
            </div>

            <button type="submit" class="btn btn-success"><b-icon-cart></b-icon-cart> Order</button>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Navbar from "@/components/Navbar.vue"
import axios from "axios"

export default {
  name: "FoodDetail",
  components: {
    Navbar,
  },
  data() {
    return {
      product: [],
    }
  },
  computed: {
    productWithImage() {
      return {
        ...this.product,
        pic: this.product.gambar && require(`../assets/images/${this.product.gambar}`)
      }
    }
  },
  // get data from backend and put it to products array above
  methods: {
    setProduct(data) {
      this.product = data
    }
  },
  mounted() {
    axios
      .get("http://localhost:3000/products/"+this.$route.params.id)
      .then((response) => this.setProduct(response.data))
      .catch((error) => console.log(error))
  }
}
</script>
