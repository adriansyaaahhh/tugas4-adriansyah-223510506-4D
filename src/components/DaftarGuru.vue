<template>
  <div class="list">
    <h2>Guru</h2>
    <ul>
      <li v-for="(guru, index) in guru" :key="index">
        {{ guru.nama }} - {{ guru.mataPelajaran }}
        <button @click="showDetail(guru)">Detail</button>
        <div v-if="selectedGuru === guru">
          <slot name="item-detail" :item="guru"></slot>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ['guru'],
  data() {
    return {
      selectedGuru: null
    };
  },
  methods: {
    showDetail(guru) {
      this.selectedGuru = guru;
      this.$emit('selected-item', guru);
    }
  }
}
</script>

<style scoped>
.list {
  flex: 1;
  padding: 15px;
  background-color: #e3f2fd;
  border-radius: 10px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

.list h2 {
  color: #1e88e5;
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
  background-color: #bbdefb;
  border-radius: 5px;
}

button {
  background-color: #1e88e5;
  color: white;
  border: none;
  padding: 5px 10px;
  cursor: pointer;
  border-radius: 5px;
  min-width: 80px; 
  outline: none;
  box-shadow: none;
}

button:hover {
  background-color: #1565c0;
}
</style>
