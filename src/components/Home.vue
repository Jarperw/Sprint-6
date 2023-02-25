<template>
  <div>
    <Escena :historia="arrayHistoria"></Escena>
  </div>
</template>

<script>
import Escena from './Escena.vue';

export default {
  name: "Home",
  components: { Escena },
  data() {
    return {
      arrayHistoria: []
    };
  },
  created() {
    fetch("/datos.json")
      .then((datos) => datos.json())
      .then((resp) => resp.map((value) => this.arrayHistoria.push(value.text)));
  },
}
</script>