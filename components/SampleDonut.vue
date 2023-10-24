<template>
    <TresMesh>
        <TresTorusGeometry :args="props.torusArgs" />
        <TresMeshBasicMaterial :color="donutColor" />
    </TresMesh>
</template>

<script setup lang="ts">
import { Color } from 'three';

interface Props {
  torusArgs: [number, number, number, number],
  torusColor: string
}

const props = defineProps<Props>()

// Ignore until step 3
const donutColor = computed(() => {
    return new Color(props.torusColor)
})
</script>