  <template>
    <TresCanvas window-size >
      <TresPerspectiveCamera :position="[0.1, 0.1, 0.1]" />
      <OrbitControls/>
      <Suspense>

        <Ring></Ring>
      </Suspense>
      <!-- <TresMesh ref="sphereRef">

        <TresSphereGeometry />
        <TresMeshNormalMaterial/>
      </TresMesh> -->
      <TresGridHelper />
    </TresCanvas>
  </template>

  <script  lang="ts" setup>
    const sphereRef = ref()
    const { onLoop } = useRenderLoop() 

    onLoop(({elapsed}) => {
      if(sphereRef.value){

        sphereRef.value.position.y = Math.sin(elapsed)
      }
    })
  </script>
