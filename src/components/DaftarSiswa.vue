<template>
  <div class="list">
    <h2>Siswa</h2>
    <ul>
      <li v-for="(siswa, index) in siswa" :key="index">
        {{ siswa.nama }} - Kelas {{ siswa.kelas }}
        <button @click="showDetail(siswa)">Detail</button>
        <div v-if="selectedSiswa === siswa">
          <slot name="item-detail" :item="siswa"></slot>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ['siswa'],
  data() {
    return {
      selectedSiswa: null
    };
  },
  methods: {
    showDetail(siswa) {
      this.selectedSiswa = siswa;
      this.$emit('selected-item', siswa);
    }
  }
}
</script>

<style scoped>
.list {
  flex: 1;
  padding: 15px;
  background-color: #e8f5e9;
  border-radius: 10px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

.list h2 {
  color: #43a047;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 10px;
  padding: 10px;
  background-color: #c8e6c9;
  border-radius: 5px;
}

button {
  background-color: #43a047;
  color: white;
  border: none;
  padding: 5px 10px;
  cursor: pointer;
  border-radius: 5px;
  outline: none;
  box-shadow: none;
  min-width: 80px; 
}

button:hover {
  background-color: #2e7d32;
}
</style>
