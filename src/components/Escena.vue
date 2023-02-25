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