<template>
  <div class="container">
    <h1>Sistem Informasi Sekolah</h1>
    <div class="lists">
      <daftar-guru :guru="guru" @selected-item="showSelectedItem"></daftar-guru>
      <daftar-siswa :siswa="siswa" @selected-item="showSelectedItem"></daftar-siswa>
      <daftar-staf :staf="staf" @selected-item="showSelectedItem"></daftar-staf>
    </div>
    <div class="detail" v-if="selectedItem">
      <h2>Detail Item</h2>
      <p>Nama: {{ selectedItem.nama }}</p>
      <p v-if="selectedItem.mataPelajaran">Mata Pelajaran: {{ selectedItem.mataPelajaran }}</p>
      <p v-if="selectedItem.kelas">Kelas: {{ selectedItem.kelas }}</p>
      <p v-if="selectedItem.departemen">Departemen: {{ selectedItem.departemen }}</p>
    </div>
  </div>
</template>

<script>
import DaftarGuru from './components/DaftarGuru.vue'
import DaftarSiswa from './components/DaftarSiswa.vue'
import DaftarStaf from './components/DaftarStaf.vue'

export default {
  components: {
    DaftarGuru,
    DaftarSiswa,
    DaftarStaf
  },
  data() {
    return {
      guru: [
        { nama: 'Alex Raim', mataPelajaran: 'Matematika' },
        { nama: 'Robby Purnomo R', mataPelajaran: 'IPA' },
        { nama: 'Varrell Bramss', mataPelajaran: 'Bahasa Inggris' }
      ],
      siswa: [
        { nama: 'Alika Mayang', kelas: '10' },
        { nama: 'Bob Williams', kelas: '11' },
        { nama: 'Eva Davis Suryono', kelas: '9' }
      ],
      staf: [
        { nama: 'Masha Rahayu', departemen: 'Administrasi' },
        { nama: 'Sara Wijundan', departemen: 'Keuangan' },
        { nama: 'Broto Dwi Yuda', departemen: 'Pemeliharaan' }
      ],
      selectedItem: null
    }
  },
  methods: {
    showSelectedItem(item) {
      this.selectedItem = item;
    }
  }
}
</script>

<style scoped>
.container {
  max-width: 900px;
  margin: 0 auto;
  padding: 20px;

  margin-top: 90px;
  background-color: #f0f0f0;
  border-radius: 10px;
  box-shadow: 0 0 20px rgba(0, 0, 0, 0.1);
}

h1 {
  text-align: center;
  color: #333;
  margin-bottom: 30px;
}

.lists {
  display: flex;
  justify-content: space-between;
  gap: 20px;
}

.detail {
  margin-top: 20px;
  padding: 15px;
  background-color: #ffffff;
  border-radius: 10px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

.detail h2 {
  margin-top: 0;
  color: #555;
}
</style>
