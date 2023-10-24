<template>
	<TresCanvas v-bind="graphicsLibraryOptions" window-size>
		<TresPerspectiveCamera :position="[0, 1.7, 7]" :look-at="[0, 0, 0]" />

		<OrbitControls :enabled="config.orbitControlsEnabled" />

		<SampleDonut />

	</TresCanvas>
</template>

<script setup>
import { OrbitControls } from '@tresjs/cientos'

const config = reactive({
	orbitControlsEnabled: true,
})

const graphicsLibraryOptions = reactive({
	clearColor: '#1C1C1C',
	powerPreference: 'high-performance',
})
</script>