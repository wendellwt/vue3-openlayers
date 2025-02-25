> [!WARNING]
> Deprecated: Please use [`ol-source-webglvector` instead](../webglvector/).
> `ol-source-webglpoints` will be removed with the next major version.

# ol-source-webglpoints

> A vector source for rendering points with WebGL

Please note, that you can't use `ol-style` and related style components here as child components.
You have to apply styles directly via the `style` prop on the `ol-webgl-points-layer` component.

<script setup>
import WebglPointsLayerDemo from "@demos/WebglPointsLayerDemo.vue"
import WebglPointsSourceDemo from "@demos/WebglPointsSourceDemo.vue"
</script>

## Usage

### with `url` prop

<ClientOnly>
<WebglPointsLayerDemo />
</ClientOnly>

::: code-group

<<< ../../../../src/demos/WebglPointsLayerDemo.vue

:::

### `ol-feature` child component

<ClientOnly>
<WebglPointsSourceDemo />
</ClientOnly>

::: code-group

<<< ../../../../src/demos/WebglPointsSourceDemo.vue

:::

## Properties

### Props from OpenLayers

Properties are passed-trough from OpenLayers directly.
Their types and default values can be checked-out [in the official OpenLayers docs](https://openlayers.org/en/latest/apidoc/module-ol_source_Vector-VectorSource.html).
Only some properties deviate caused by reserved keywords from Vue / HTML.
This deviating props are described in the section below.

### Deviating Properties

None.

## Events

You have access to all Events from the underlying source.
Check out [the official OpenLayers docs](https://openlayers.org/en/latest/apidoc/module-ol_source_Vector-VectorSource.html) to see the available events tht will be fired.

```html
<ol-source-webglpoints :url="url" @error="handleEvent" />
```

## Methods

You have access to all Methods from the underlying source.
Check out [the official OpenLayers docs](https://openlayers.org/en/latest/apidoc/module-ol_source_Vector-VectorSource.html) to see the available methods.

To access the source, you can use a `ref()` as shown below:

```vue
<template>
  <!-- ... -->
  <ol-source-webglpoints :url="url" ref="sourceRef" />
  <!-- ... -->
</template>

<script setup lang="ts">
import { ref, onMounted } from "vue";
import type VectorSource from "ol/source/vector";

const sourceRef = ref<{ source: VectorSource }>(null);

onMounted(() => {
  const source: VectorSource = sourceRef.value?.source;
  // call your method on `source`
});
</script>
```
