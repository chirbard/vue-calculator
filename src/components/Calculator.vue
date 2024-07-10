<template>
  <div class="flex flex-col w-fit h-min bg-[#0d1117] p-4 rounded-lg border-2 border-[#42414d] text-[#a0a5ac]">
    <div class="flex justify-center bg-[#ffffff] mb-2 rounded-md p-2">{{ display }}</div>
    <div class="grid grid-cols-4 gap-2">
      <button v-for="button in buttons" :key="button" @click="handleClick(button)"
        class="p-4 bg-[#0d1117] border-2 border-[#7f44c5] rounded-md text-white">
        {{ button }}
      </button>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';

export default defineComponent({
  name: 'Calculator',
  setup() {
    const display = ref<string>('0');
    const buttons = ref<string[]>([
      '7', '8', '9', '/',
      '4', '5', '6', '*',
      '1', '2', '3', '-',
      '0', '.', '+', '='
    ]);

    const handleClick = (button: string) => {
      if (button === '=') {
        try {
          display.value = eval(display.value).toString();
        } catch (e) {
          display.value = 'Error';
        }
      } else {
        display.value === '0' ? display.value = button : display.value += button;
      }
    };

    return {
      display,
      buttons,
      handleClick
    };
  }
});
</script>