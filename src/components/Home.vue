<template>
  <div v-if="inicio" class="inicio">
    <h1>Lorem ipsum dolor sit amet consectetur adipisicing elit. Quibusdam beatae iste itaque, laborum totam illum deleniti soluta, aliquam, repudiandae neque rerum id corrupti asperiores in perferendis modi dolor ad nisi.</h1>
    <button @click="inicio = !inicio">Comenzar</button>
  </div>
  <div v-else>
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
      currentSentence: 0,
      inicio: true
    };
  },
  created() {
    fetch("/datos.json")
      .then((datos) => datos.json())
      .then((resp) => resp.map((value) => this.arrayHistoria.push(value.text)));
  },
}
</script>

<style scoped>
.inicio {
  display: flex;
  flex-direction: column;
  align-items: center;
  font-family: cursive;
  text-align: center;
  margin: 5em
}

.inicio button {
  font-family: cursive;
  background: #000;
  color: #fff;
  border: 0.1em solid #000;
  border-radius: 0.7em;
  padding: 0.8em 2em;
  margin: 4em;
}

.inicio button:hover {
  border: 0.22em solid #000;
}

.inicio button:active {
  background: #fff;
  color: #000;
}

@media (max-width: 992px) {
  .inicio {
    font-size: smaller;
    margin-top: 7em;
  }

  .inicio button {
    padding: 0.7em 1.9em;
  }
}

@media (max-width: 768px) {
  .inicio {
    font-size: 0.7em;
    margin: 2em;
    margin-top: 8em;
  }

  .inicio button {
    padding: 0.65em 1.85em;
  }
}

@media (max-width: 576px) {
  .inicio {
    font-size: 0.65em;
  }
} 
</style>