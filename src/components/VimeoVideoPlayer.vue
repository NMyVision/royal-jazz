<script setup lang="ts">
import { computed } from "vue"

type Props = {
  videoId: string | number
  title: string
  hostId?: string // 'h' parameter, typically for private videos/portfolios
  showBadge?: boolean // 'badge' parameter
  autoPause?: boolean // 'autopause' parameter
  playerId?: number // 'player_id' parameter
  appId?: number // 'app_id' parameter
  loopVideo?: boolean // 'loop' parameter
  autoPlay?: boolean // 'autoplay' parameter
  muted?: boolean // 'muted' parameter
  controls?: boolean // 'controls' parameter (show/hide player controls)
  dnt?: boolean // 'dnt' (Do Not Track) parameter
}

// Destructure props with default values
const {
  videoId,
  title,
  hostId,
  showBadge = false,
  autoPause = false,
  playerId = 0,
  appId = 58479,
  loopVideo = true, // Matches original hardcoded value
  autoPlay = false,
  muted = false,
  controls = true,
  dnt = false,
} = defineProps<Props>()

const vimeoSrc = computed(() => {
  const params: Record<string, string | number> = {
    badge: showBadge ? 1 : 0,
    autopause: autoPause ? 1 : 0,
    player_id: playerId,
    app_id: appId,
    loop: loopVideo ? 1 : 0,
    autoplay: autoPlay ? 1 : 0,
    muted: muted ? 1 : 0,
    controls: controls ? 1 : 0,
    dnt: dnt ? 1 : 0,
  }

  // Conditionally add hostId if it exists
  if (hostId) {
    params.h = hostId
  }

  // Construct the query string from the parameters
  const queryString = Object.entries(params)
    .map(([key, value]) => `${key}=${value}`)
    .join("&")

  return `https://player.vimeo.com/video/${videoId}?${queryString}`
})
</script>

<template>
  <div style="padding: 56.25% 0 0 0; position: relative">
    <iframe
      :src="vimeoSrc"
      frameborder="0"
      allow="fullscreen; picture-in-picture; clipboard-write"
      style="position: absolute; top: 0; left: 0; width: 100%; height: 100%"
      :title="title"
    ></iframe>
  </div>
</template>