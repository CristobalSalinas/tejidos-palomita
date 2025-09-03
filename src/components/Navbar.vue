<script setup lang="ts">
import { Motion } from "motion-v";
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
    <Motion 
        as="nav"
        class="bg-black text-white text-center rounded-lg fixed left-1/2 transform -translate-x-1/2 z-50 top-4 px-5 py-2"
        :initial="{width: '256px'}"
        :animate="{width: isHovered ? '180px' : '256px' }"
        :transition="{ duration: 0.3, ease: 'easeInOut' }"
        @mouseenter="handleMouseEnter"
        @mouseleave="handleMouseLeave">
        <p>Tejidos Palomita</p>
    </Motion>
</template>