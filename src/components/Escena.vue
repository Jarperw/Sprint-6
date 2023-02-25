<template>
  <div>
    <p
      :class="{ activo: currentSentence == index }" 
      v-for="(item, index) in historia" 
      :key="index"
    >
      {{ item.text }}
    </p>
    <div class="fondo" :style="mostrarImagen"></div>
  </div>
</template>

<script>
export default {
  name: 'Escena',
  props: ["historia", "currentSentence"],
  data() {
    return {
      img: ''
    }
  },
  computed: {
    mostrarImagen() {
      return this.img = { backgroundImage: `url(${this.historia[this.currentSentence].img})` }
    }
  }
}
</script>

<style scoped>
p {
  text-align: center;
  padding: 1em;
  margin: 1.2em;
  border: 0.13em solid #000;
  border-radius: 3em;
  background-color: #fffa;
}

.activo {
  background: #f99;
}

.fondo {
  position: fixed;
  z-index: -1;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-size: cover;
  background-position: center;
}

@media (max-width: 992px) {
  p {
    font-size: smaller;
    border: 0.15em solid #000;
  }
}

@media (max-width: 768px) {
  p {
    font-size: 0.73em;
    border: 0.172em solid #000;
  }
}
</style>