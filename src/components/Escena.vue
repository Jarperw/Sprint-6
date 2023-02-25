<template>
  <div>
    <p v-for="(item, index) in historia" :key="index">
      {{ item }}
    </p>
  </div>
</template>

<script>
export default {
  name: 'Escena',
  props: ["historia"]
}
</script>

<style scoped>
p {
  text-align: center;
  padding: 1em;
  margin: 1.2em;
  border: 0.13em solid #000;
  border-radius: 3em;
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