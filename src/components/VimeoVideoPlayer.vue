<script setup lang="ts">
type Props = {
  videoId: string | number
  title: string
  hostId: string
}
const { videoId, title, hostId } = defineProps<Props>()
</script>

<template>
  <div style="padding: 56.25% 0 0 0; position: relative"><iframe :src="`https://player.vimeo.com/video/${videoId}?h=${hostId}&amp;badge=0&amp;autopause=0&amp;player_id=0&amp;app_id=58479&amp;loop=1&amp;autoplay=0&amp;muted=0`" frameborder="0" allow="fullscreen; picture-in-picture; clipboard-write" style="position: absolute; top: 0; left: 0; width: 100%; height: 100%" :title></iframe></div>
</template>
