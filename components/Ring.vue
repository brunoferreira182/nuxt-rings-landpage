<script setup lang="ts">
import { Mesh, MeshBasicMaterial } from 'three';
const {scene: model, nodes} = await useGLTF('./flowerRing/flower-silver-ring.glb')
// const ringTexture = await useTexture(['./OneRing_emissive.png'])
// const ringBakedMaterial = new MeshBasicMaterial({
//   map: ringTexture
// })
// ringTexture.flipY = false
// nodes.OneRing_OneRing_0.material = ringBakedMaterial
console.log(nodes, 'opoakdpoak')
</script>

<template>
  <primitive :object="nodes.acua_acua_0
" />
</template>

