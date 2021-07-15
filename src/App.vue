<template>
  <Title title="Aplikasi Pengeluaran Sederhana"></Title>
  <FormPengeluaran @listAdded="tambahPengeluaran($event)"></FormPengeluaran>
  <div class="total">
    <h3>Total Pengeluaran : Rp. {{ totalPengeluaran }},-</h3>
  </div>
  <ListPengeluaran v-if="dataPengeluaran.length" :data-pengeluaran="dataPengeluaran"></ListPengeluaran>
</template>

<script>
import { ref, watch, reactive } from 'vue';
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

  setup() {
    const dataPengeluaran = reactive([]);
    let totalPengeluaran = ref(0);

    function tambahPengeluaran(data) {
      dataPengeluaran.push(data);
    }

    watch(dataPengeluaran, () => {
      totalPengeluaran.value = dataPengeluaran.reduce((acc, curr) => acc + parseInt(curr.nominal), 0);
    });

    return { dataPengeluaran, tambahPengeluaran, totalPengeluaran };
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
