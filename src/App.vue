<template>
  <Title title="Aplikasi Pengeluaran Sederhana"></Title>
  <FormPengeluaran @listAdded="tambahData($event)"></FormPengeluaran>
  <div class="total">
    <h3>Total Pengeluaran : Rp. {{ totalPengeluaran }},-</h3>
  </div>
  <ListPengeluaran v-if="cekData" :data-pengeluaran="dataPengeluaran"></ListPengeluaran>
</template>

<script>
import Title from "@/components/Title";
import ListPengeluaran from "@/components/ListPengeluaran";
import FormPengeluaran from "@/components/FormPengeluaran";

export default {
  name: 'App',
  components: {
    Title,
    ListPengeluaran,
    FormPengeluaran
  },
  data() {
    return {
      dataPengeluaran : [],
    }
  },
  methods: {
    tambahData(event) {
      this.dataPengeluaran.push(event);
    }
  },
  computed: {
    cekData() {
      return this.dataPengeluaran.length;
    },
    totalPengeluaran() {
      return this.dataPengeluaran.reduce((acc, cur) => acc + parseInt(cur.nominal), 0)
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
