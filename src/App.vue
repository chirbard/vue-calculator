<template>
  <div class="flex column justify-center items-center h-screen bg-[#0d1117]">
    <Calculator />
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import Calculator from './components/Calculator.vue';

export default defineComponent({
  name: 'App',
  components: {
    Calculator
  }
});
</script>