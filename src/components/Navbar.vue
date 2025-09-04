<script setup lang="ts">
import { Motion, AnimatePresence } from "motion-v";
import { ref } from "vue";

const isHovered = ref(false);

const handleMouseEnter = () => {
  isHovered.value = true;
};

const handleMouseLeave = () => {
  isHovered.value = false;
};
</script>

<template>
  <div 
    id="navbar" 
    class="fixed left-1/2 transform -translate-x-1/2 top-4 z-60 flex flex-col items-center"
    @mouseenter="handleMouseEnter" 
    @mouseleave="handleMouseLeave">
    <Motion as="nav"
      class="bg-black text-white text-center z-50 px-5 py-2"
      :class="{'rounded-lg': !isHovered, 'rounded-t-lg':isHovered}"
      :initial="{ width: '256px' }" 
      :animate="{ width: isHovered ? '180px' : '256px' }"
      :transition="{ duration: 0.3, ease: 'easeInOut' }">
      <p>Tejidos Palomita</p>
    </Motion>
    <AnimatePresence>
      <Motion v-if="isHovered" as="div"
        class="bg-black text-white text-center z-40 px-5 py-2 rounded-lg"
        :initial="{ y: -40, width: '256px' }" 
        :animate="{ y: 0, width: '300px'}"
        :transition="{ duration: 0.3, ease: 'easeInOut' }" 
        :exit="{ y: -40, width: '256px'}">
        <p>Menú secundario</p>
      </Motion>
    </AnimatePresence>
  </div>
</template>