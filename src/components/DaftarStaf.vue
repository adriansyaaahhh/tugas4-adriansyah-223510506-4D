<template>
  <div class="list">
    <h2>Staf</h2>
    <ul>
      <li v-for="(staf, index) in staf" :key="index">
        {{ staf.nama }} - {{ staf.departemen }}
        <button @click="showDetail(staf)">Detail</button>
        <div v-if="selectedStaf === staf">
          <slot name="item-detail" :item="staf"></slot>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ['staf'],
  data() {
    return {
      selectedStaf: null
    };
  },
  methods: {
    showDetail(staf) {
      this.selectedStaf = staf;
      this.$emit('selected-item', staf);
    }
  }
}
</script>

<style scoped>
.list {
  flex: 1;
  padding: 15px;
  background-color: #fff3e0;
  border-radius: 10px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

.list h2 {
  color: #fb8c00;
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
  background-color: #ffe0b2;
  border-radius: 5px;
}

button {
  background-color: #fb8c00;
  color: white;
  border: none;
  padding: 5px 10px;
  cursor: pointer;
  border-radius: 5px;
  outline: none;
  min-width: 80px; 
}

button:hover {
  background-color: #ef6c00;
}
</style>
