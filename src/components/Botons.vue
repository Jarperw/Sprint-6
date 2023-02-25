<template>
  <div>
    <button @click="anterior">Anterior</button>
    <button @click="siguiente">Siguiente</button>
  </div>
</template>
  
<script>
export default {
  name: "Botons",
  props: ["historia"],
  data() {
    return {
      count: 0,
    };
  },
  methods: {
    anterior() {
      this.count == 0 ? this.count : this.count--;
      this.$emit("contador", this.count);
    },
    siguiente() {
      this.count == this.historia.length - 1 ? this.count : this.count++;
      this.$emit("contador", this.count);
    },
  },
};
</script>
  
<style scoped>
button {
  width: 50%;
  padding: 1em;
  font-size: 1.6em;
}

@media (max-width: 768px) {
  button {
    font-size: 1.5em;
  }
}

@media (max-width: 576px) {
  button {
    font-size: 1.4em;
  }
}
</style>