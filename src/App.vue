<script setup>
import { ref } from 'vue'
const num = ref(0)
function addNum() {
  num.value++
}
</script>

<template>
  <div>
    {{ num }}
    <button type="button" v-on:click="addNum">+</button>
  </div>
</template>
