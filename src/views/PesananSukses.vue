<template>
  <div class="pesanan-sukses">
    <Navbar />
    <h2>Pesanan Sukses</h2>
  </div>
</template>

<script>
import Navbar from "@/components/Navbar.vue";

export default {
  name: "PesananSukses",
  data() {
    return {
      keranjangs: [],
    };
  },
  components: {
    Navbar,
  },
};
</script>

<style>
</style>

