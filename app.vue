<template>
  <div>
    <div class="header">
      <div class="title">Évora</div>
      <div class="buttons">
        <button>&#x2302; <!-- Home icon --></button>
        <button>&#9881; <!-- Settings icon --></button>
      </div>
    </div>

    <div class="content">
      <TresCanvas window-size>
        <TresPerspectiveCamera :position="[0.1, 0.1, 0.1]" />
        <OrbitControls />
        <Suspense>
          <Ring></Ring>
        </Suspense>
        <!-- <TresMesh ref="sphereRef">
          <TresSphereGeometry />
          <TresMeshNormalMaterial/>
        </TresMesh> -->
        <!-- <TresGridHelper /> -->
      </TresCanvas>
    </div>
  </div>
</template>

<script lang="ts" setup>
const sphereRef = ref()
const { onLoop } = useRenderLoop()

onLoop(({ elapsed }) => {
  if (sphereRef.value) {
    sphereRef.value.position.y = Math.sin(elapsed)
  }
})
</script>

<style scoped>
body, html {
  margin: 0;
  padding: 0;
  width: 100%;
  height: 100%;
  overflow: hidden;
}
.header {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 56px;
  background-color: #f8f8f8;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 16px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  z-index: 10;
}
.header .title {
  font-size: 20px;
  font-weight: bold;
}
.header .buttons {
  display: flex;
}
.header .buttons button {
  background: none;
  border: none;
  font-size: 20px;
  margin-left: 16px;
  cursor: pointer;
}
.content {
  position: absolute;
  top: 56px; /* altura do header */
  left: 0;
  right: 0;
  bottom: 0;
}
</style>
