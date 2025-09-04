<script setup lang="ts">
const props = defineProps({
    to:{
        type:String,
        default:'#',
    },
    text:{
        type:String,
        default:'Link',
    }
})
</script>

<template>
    <div class="h-12 w-24 bg-white text-black rounded-lg flex items-center justify-center">
        <a :href="to">{{ text.toUpperCase() }}</a>
    </div>
</template>