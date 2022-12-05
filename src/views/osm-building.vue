<template>
  <cesium-map @select="handleSelect" @map-ready="mapReady" v-model="value" />
  <panel-menu v-model:visible="panelVisible" />
</template>
<script setup lang="ts">
  import { ref } from 'vue'
  import { useRouter } from 'vue-router'
  import useSetOSMBuildings from '/@/hooks/demo/setOSMBuildings'

  const router = useRouter()
  const value = ref<string>('osm')

  const handleSelect = (value: string) => {
    router.push({ name: value })
  }
  const panelVisible = ref<boolean>(false)

  const mapReady = () => {
    useSetOSMBuildings(window.CViewer)
  }
</script>
