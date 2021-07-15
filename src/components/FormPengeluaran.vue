<template>
  <form @submit.prevent="tambahkanList">
    <div class="form-input">
      <label for="number">Nominal</label>
      <input type="number" v-model="dataPengeluaran.nominal" id="number">
    </div>
    <div class="form-input">
      <label for="keterangan">Keterangan</label>
      <input type="text" v-model="dataPengeluaran.keterangan" id="keterangan">
    </div>
    <div>
      <button type="submit">Simpan</button>
    </div>
  </form>
</template>

<script>
import { reactive } from 'vue';
export default {
  name: "FormPengeluaran",
  setup(props, context) {
    const dataPengeluaran = reactive({
      nominal: null,
      keterangan: null,
    });

    function tambahkanList() {
      context.emit('listAdded', {
        nominal: dataPengeluaran.nominal,
        keterangan: dataPengeluaran.keterangan,
      });
      dataPengeluaran.nominal = null;
      dataPengeluaran.keterangan = null;
    }

    return { dataPengeluaran, tambahkanList };
  }
}
</script>

<style scoped>
  form {
    display: flex;
    justify-content: center;
    align-items: center;
    margin-bottom: 10px;
  }

  label {
    margin-right: 10px;
  }

  .form-input {
    margin: 5px 5px 10px;
  }

  input {
    padding: 7px 5px;
  }

  button {
    padding: 9px 13px;
    background-color: #5a25dd;
    margin-bottom: 5px;
    margin-left: 5px;
    color: #eaeaea;
    border: none;
    border-radius: 3px;
  }

  button:hover {
    cursor: pointer;
    background-color: #490ae7;
  }
</style>