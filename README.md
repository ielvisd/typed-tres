# Using the Composition API with TypeScript to type component props

**Instructions:**

- Download/fork the [project boilerplate](https://github.com/ielvisd/typed-tres)
- Install pinia via npm (or yarn if you prefer) and run the project

You should see a pink donut on your screen, feel free zoom to spin it around!

![Screenshot 2023-10-24 at 2.04.18 PM.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/a7b4e22d-75fa-4e6a-8223-268fcde646e1/52faead6-27fa-4254-a4b2-0764bf32a290/Screenshot_2023-10-24_at_2.04.18_PM.png)

You have a MyScene and a SampleDonut component with the following templates, I recommend you explore them and the [TreJsS](https://tresjs.org/) documentation for a bit if this is your first time using TresJS.

**MyScene.client.vue**

```
<template>
	<TresCanvas v-bind="graphicsLibraryOptions" window-size>
		<TresPerspectiveCamera :position="[0, 1.7, 7]" :look-at="[0, 0, 0]" />

		<OrbitControls :enabled="config.orbitControlsEnabled" />

		<SampleDonut />

	</TresCanvas>
</template>

<script setup  >
import { OrbitControls } from '@tresjs/cientos'

const config = reactive({
	orbitControlsEnabled: true,
})

const graphicsLibraryOptions = reactive({
	clearColor: '#1C1C1C',
	powerPreference: 'high-performance',
})
</script>
```

**SampleDonut.vue**

```
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
```

Your task is to enhance this component using the Composition API and TypeScript to define typed props for better code safety.

1. Add **`lang="ts"`** to the **`<script setup">`** section of both components to utilize TypeScript with the Composition API.
2. In this section, in the SampleDonut component create a SampleDonutProps interface. This interface should specify the props needed for the Donut component:
    - **`torusArgs`**: An array of numbers that define the torus/donut.
        - Use this as the passed prop value: [1, 0.5, 16, 32]
    - **`torusColor`**: A string value.
        - Use your favorite CSS color string/value
3. Replace the hardcoded values in `**SampleDonut.vue**` with props passed from `**MyScene.Client.vue**`. Use the **`donutColor`** computed property to correctly type to a `**Color**` class as the TresMeshBasicMaterial expects a special `Color` class and not a simple string.
****

✅ When complete, you should be able to control the color and donut shape properties through the typed props. You should not see any TypeScript errors and are on your way to building robust type safe Vue applications with the Composition API!