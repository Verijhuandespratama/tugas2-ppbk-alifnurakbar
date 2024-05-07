<template>
  <div>
    <!-- Elemen HTML yang berbeda -->
    <h1>Alif Nur Akbar</h1>
    <p>Welcome to My Web Page!</p>
    
    <!-- Elemen input teks -->
    <input type="text" v-model="textInput" @input="updateText">

    <!-- Elemen dengan class bindings dan style bindings -->
    <div :class="{ 'highlight': isHighlighted }" :style="{ 'font-size': fontSize + 'px' }">
      Teks akan berubah warna merah.
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      textInput: '',
      isHighlighted: false,
      fontSize: 16
    };
  },
  methods: {
    updateText(event) {
      this.textInput = event.target.value;
    },
    toggleHighlight() {
      this.isHighlighted = !this.isHighlighted;
    }
  },
  mounted() {
    // Menambahkan event listener untuk merubah nilai isHighlighted
    this.$el.addEventListener('mouseover', this.toggleHighlight);
    this.$el.addEventListener('mouseout', this.toggleHighlight);
  },
  beforeDestroy() {
    // Membersihkan event listener saat komponen dihancurkan
    this.$el.removeEventListener('mouseover', this.toggleHighlight);
    this.$el.removeEventListener('mouseout', this.toggleHighlight);
  }
};
</script>

<style scoped>
/* Style untuk highlight */
.highlight {
  background-color: darkred;
}

/* Style untuk elemen dengan style bindings */
div {
  border: 1px solid rgb(250, 5, 5);
  padding: 10px;
  margin-top: 10px;
}
</style>
