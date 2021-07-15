<template>
  <div class="table">
    <table>
      <tr>
        <th>Nominal</th>
        <th>Keterangan</th>
      </tr>
      <tr v-for="(pengeluaran,index) in dataPengeluaran" :key="index">
        <td>{{ pengeluaran.nominal }}</td>
        <td>{{ pengeluaran.keterangan }}</td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  name: "ListPengeluaran",
  props: ['dataPengeluaran'],
}
</script>

<style scoped>
  table, th, td {
    border-collapse: collapse;
    border: 1px solid black;
    align-items: center;
  }

  table {
    text-align: center;
    width: 700px;
    margin: auto;
  }
  
  th {
    background-color: #5a25dd;
    padding: 10px;
    color: #eaeaea;
  }

  td {
    padding: 10px;
  }

  td:hover {
    background-color: #eaeaea;
    cursor: pointer;
  }
</style>