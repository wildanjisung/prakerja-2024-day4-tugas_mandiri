<script>
export default {
  data() {
    return {
      item: '',
      list: [],
      isErrorInput: false
    }
  },
  methods: {
    simpan() {
      // validasi
      if(this.item == '') {
        this.isErrorInput = true
      } else {
        // fungsi simpan ke array
        this.list.push(this.item)
        
        // reset inputbox
        this.item = '';

        // remove error message
        this.isErrorInput = false
      }

    }
  },
  computed: {
    isMoreThanFour: function () {
      return this.list.length >= 4;
    }
  },
}

</script>

<template>
  <!-- list -->
  <ul>
    <li v-for="(todo, index) in list" :key="index">{{ todo }}</li>
  </ul>

  <!-- input -->
  <input type="text" v-model="item">
  <button @click="simpan">Simpan</button>
  <p v-if="isErrorInput" class="text-error">Inputan tidak boleh kosong</p>
  <p v-if="isMoreThanFour">{{ 'Hebat' }}</p>
</template>

<style scoped>
.text-error {
  background-color: red;
  color: white;
}
</style>
