<template>
  <div>
    <Botons
      @contador="currentSentence = $event"
      :historia="arrayHistoria"
    ></Botons>
    <Escena
      :historia="arrayHistoria"
      :currentSentence="currentSentence"
    ></Escena>
  </div>
</template>

<script>
import Escena from './Escena.vue';
import Botons from './Botons.vue';

export default {
  name: "Home",
  components: { Escena, Botons },
  data() {
    return {
      arrayHistoria: [],
      currentSentence: 0
    };
  },
  created() {
    fetch("/datos.json")
      .then((datos) => datos.json())
      .then((resp) => resp.map((value) => this.arrayHistoria.push(value.text)));
  },
}
</script>