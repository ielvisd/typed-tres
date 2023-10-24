<template>
    <TresMesh>
        <TresTorusGeometry :args="[1, 0.5, 16, 32]" />
        <TresMeshBasicMaterial color="pink" />
    </TresMesh>
</template>

<script setup>
import { Color } from 'three';

// Ignore until step 3
const donutColor = computed(() => {
    return new Color(props.color)
})
</script>